# Building a Flask API with Route Creation Error Handling and HTTP Requests

This Flask application serves as an API for managing a list of people's data. It includes endpoints for retrieving, adding, and deleting data, as well as searching for specific individuals by name.

## Getting Started

### Prerequisites
- Python 3x
- Flask

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/flask-data-api.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Flask application:
   ```bash
   flask run
   ```

## Endpoints
- `/`
  - `GET`: Returns a simple "hello world" message.
- `/noconent`
  - `GET`: Returns a "No content found" message with a status code of `204` (No Content).
- `/exp`
  - `GET`: Returns a "Hello World" message with an explicit status code of `200`.
- `/data`
  - `GET`: Returns a message indicating the length of the data if data is available.
    - If data is empty, returns "Data is empty" with a status code of `500` (Internal Server Error).
    - If data is not defined, returns "Data not found" with a status code of `404` (Not Found). 
- `/name_search`
  - `GET`: Search for a person by first name.
    - Parameters:
      - `q`: Query parameter for the first name to search.
    - Returns:
      - If found, returns the person's data with a status code of `200` (OK).
      - If not found, returns "Person not found" with a status code of `404` (Not Found).
      - If `q` parameter is missing, returns "Invalid input parameter" with a status code of `422` (Unprocessable Entity). 
- `/count`
  - `GET`: Returns the count of data entries.
    - Returns the count of data entries with a status code of `200` (OK).
    - If data is not defined, returns "Data not defined" with a status code of `500` (Internal Server Error).   
- `/person/<uuid:id>`
  - `GET`: Find a person by their unique identifier.
    - Returns the person's data if found with a status code of `200` (OK).
    - If person is not found, returns "Person not found" with a status code of `404` (Not Found).
  - `DELETE`: Delete a person by their unique identifier.
    - Deletes the person's data if found with a status code of `200` (OK).
    - If person is not found, returns "Person not found" with a status code of `404` (Not Found). 
- `/person`
  - `POST`: Add a new person.
    - Accepts a JSON object representing a new person.
    - Adds the new person to the data if valid with a status code of `200` (OK).
    - If input parameter is missing or invalid, returns "Invalid input parameter" with a status code of `422` (Unprocessable Entity).
    - If data is not defined, returns "Data not defined" with a status code of `500` (Internal Server Error).

## Error Handling
- `404`: Returns "API not found" with a status code of 404 (Not Found) for undefined endpoints.
- `500`: Returns "Internal Server Error" with a status code of 500 (Internal Server Error) for unexpected errors.
