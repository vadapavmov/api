# vadapav.mov API Documentation

Welcome to the Vadapav API documentation! This API is designed for accessing and managing a collection of movies and TV series. Below, you'll find detailed information about the available endpoints and how to use them.

## Base URL

All URLs referenced in the documentation have the following base:

```
https://vadapav.mov/api
```

## Endpoints

### 1. Retrieve Root Directory

- **Endpoint:** `/d`
- **Method:** `GET`
- **Description:** Retrieves the root directory of the collection.
- **Response:**
  - `message`: Description of the response.
  - `data`: Object containing directory details.
    - `id`: Unique identifier of the directory.
    - `name`: Name of the directory.
    - `dir`: Boolean indicating if it's a directory.
    - `mtime`: Last modified time.
    - `files`: Array of files/directories in the root directory.

#### Example Request:

```
GET https://vadapav.mov/api/d
```

#### Example Response:

```json
{
  "message": "directory retrieved",
  "data": {
    "id": "11111111-1111-1111-1111-111111111111",
    "name": "",
    "dir": true,
    "mtime": "2023-06-29T01:33:04.737547Z",
    "files": [
      // Array of file objects
    ]
  }
}
```

### 2. Retrieve Specific Directory

- **Endpoint:** `/d/{dir_id}`
- **Method:** `GET`
- **Description:** Retrieves a specific directory by its ID.
- **Path Parameters:**
  - `dir_id`: Unique identifier of the directory.

#### Example Request:

```
GET https://vadapav.mov/api/d/{dir_id}
```

#### Example Response:

```json
{
  "message": "directory retrieved",
  "data": {
    // Directory details
  }
}
```

### 3. Search for Files/Directory

- **Endpoint:** `/s/{query}`
- **Method:** `GET`
- **Description:** Performs a search in the collection based on the provided query.
- **Path Parameters:**
  - `query`: Search term.

#### Example Request:

```
GET https://vadapav.mov/api/s/{query}
```

#### Example Response:

```json
{
  "message": "search result retrieved",
  "data": [
    // Array of search results
  ]
}
```

## Rate Limiting

The Vadapav API enforces rate limiting to ensure fair usage and prevent abuse. The rate limit is measured against the IP address of the requesting user.

- **Current Limit:** 60 API calls per 30 seconds.

### Rate Limit Headers

The API includes the following headers in the response to help you track your usage against the rate limit:

- `x-ratelimit-limit`: The maximum number of allowed requests in the current time window.
- `x-ratelimit-remaining`: The number of requests remaining in the current time window.
- `x-ratelimit-reset`: The time at which the current rate limit window resets in UTC epoch seconds.

## Usage Guidelines
- Avoid making unnecessary or excessively frequent requests to the API.
- Handle responses and errors gracefully in your application.
- Be mindful of the rate limits to avoid service disruptions.


----
