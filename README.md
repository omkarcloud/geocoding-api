# Geocoding API

Free and Unlimited API to convert city names to latitude/longitude coordinates. Example Response:
```json
{
  "name": "New York",
  "state": "New York",
  "country_code": "US",
  "coordinates": {
    "latitude": 40.7127281,
    "longitude": -74.0060152
  }
}
```

## Features

- Convert any city name to lat/long coordinates
- Completely free and unlimited - no rate limits, no usage caps
- Once the Geolocation API is perfected, we will open source it by February 25, 2026.
- Filter by state and country code for accuracy
- Covers cities worldwide
- High Quality Api, Built by [Omkar Cloud](https://github.com/omkarcloud), a pro open source organization ([creators of Botasaurus](https://github.com/omkarcloud/botasaurus), 3.8K+ GitHub stars)


## Authentication

1. Create account at [omkar.cloud](https://www.omkar.cloud/auth/sign-up)

![Sign Up](https://raw.githubusercontent.com/omkarcloud/assets/master/images/signup.png)

2. Get API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key)

![Copy API Key](https://raw.githubusercontent.com/omkarcloud/assets/master/images/enrichment-key-omkar.png)

3. Include `API-Key` header in requests

## Quick Start

```bash
curl -X GET "https://geocoding-api.omkar.cloud/geocode?city=New%20York" \
  -H "API-Key: YOUR_API_KEY"
```

```json
[
  {
    "name": "New York",
    "state": "New York",
    "country_code": "US",
    "coordinates": {
      "latitude": 40.7127281,
      "longitude": -74.0060152
    }
  }
]
```

## Installation

### Python

```bash
pip install requests
```

```python
import requests

response = requests.get(
    "https://geocoding-api.omkar.cloud/geocode",
    params={"city": "New York"},
    headers={"API-Key": "YOUR_API_KEY"}
)

data = response.json()[0]
print(f"Coordinates: {data['coordinates']['latitude']}, {data['coordinates']['longitude']}")
```

### Node.js

```bash
npm install axios
```

```javascript
import axios from "axios";

const response = await axios.get("https://geocoding-api.omkar.cloud/geocode", {
    params: { city: "New York" },
    headers: { "API-Key": "YOUR_API_KEY" }
});

console.log(`Coordinates: ${response.data[0].coordinates.latitude}, ${response.data[0].coordinates.longitude}`);
```

## API Reference

### Endpoint

```
GET https://geocoding-api.omkar.cloud/geocode
```

### Headers

| Header | Required | Description |
|--------|----------|-------------|
| `API-Key` | Yes | API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key) |

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `city` | Yes | City name to geocode (e.g., "London", "Tokyo") |
| `state` | No | State/region to disambiguate same-named cities |
| `country_code` | No | Two-letter ISO country code (e.g., "US", "GB", "JP") |

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | City/place name |
| `state` | string | State or province |
| `country_code` | string | Two-letter ISO country code |
| `coordinates` | object | Contains `latitude` and `longitude` |

## Examples

### Basic city lookup

```python
response = requests.get(
    "https://geocoding-api.omkar.cloud/geocode",
    params={"city": "London"},
    headers={"API-Key": "YOUR_API_KEY"}
)

location = response.json()[0]
print(f"{location['name']}: {location['coordinates']['latitude']}, {location['coordinates']['longitude']}")
```

### Filter by country

```python
response = requests.get(
    "https://geocoding-api.omkar.cloud/geocode",
    params={
        "city": "Paris",
        "country_code": "FR"
    },
    headers={"API-Key": "YOUR_API_KEY"}
)

location = response.json()[0]
print(f"{location['name']}, {location['country_code']}")
```

### Filter by state (US cities)

```python
response = requests.get(
    "https://geocoding-api.omkar.cloud/geocode",
    params={
        "city": "Portland",
        "state": "Oregon"
    },
    headers={"API-Key": "YOUR_API_KEY"}
)

location = response.json()[0]
print(f"{location['name']}, {location['state']}")
```

## Error Handling

```python
response = requests.get(
    "https://geocoding-api.omkar.cloud/geocode",
    params={"city": "New York"},
    headers={"API-Key": "YOUR_API_KEY"}
)

if response.status_code == 200:
    data = response.json()
elif response.status_code == 401:
    # Invalid API key
    pass
```

## Rate Limits

**No limits!** This API is completely free with unlimited requests.

## Questions? We have answers.

Reach out anytime. We will solve your query within 1 working day.

[![Contact Us on WhatsApp about Geocoding API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/whatsapp-us.png)](https://api.whatsapp.com/send?phone=918178804274&text=I%20have%20a%20question%20about%20the%20Geocoding%20API.)

[![Contact Us on Email about Geocoding API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/ask-on-email.png)](mailto:happy.to.help@omkar.cloud?subject=Geocoding%20API%20Question)
