# Unit.Converter

A RESTful Unit Conversion API built with **ASP.NET Core Minimal API**. The API converts numerical values between different units of measurement, with support for **length, temperature, and weight/mass** conversions.

The project is designed as a maintainable real-world solution, with a clear project structure and an approach that can be extended to support hundreds of units and additional conversion categories in the future.

## Features

- RESTful HTTP API for unit conversion
- Length conversions
- Weight/mass conversions
- Temperature conversions
- Input validation
- Clear HTTP responses for invalid requests
- Easily extensible conversion architecture
- No external NuGet packages required
- Built with .NET 10

## Supported Conversions

### Length

- Meters
- Kilometers
- Centimeters
- Millimeters
- Miles
- Yards
- Feet
- Inches

### Weight / Mass

- Kilograms
- Grams
- Milligrams
- Pounds
- Ounces

### Temperature

- Celsius
- Fahrenheit
- Kelvin

Additional units and conversion categories can be added as the application evolves.

## API Usage

The API exposes an endpoint that accepts a value, source unit, target unit, and conversion category.

Example:

```http
GET  http://localhost:5197/api/convert?category=length&from=meters&to=feet&value=10


Example response:

{
  "value": 10,
  "from": "meters",
  "to": "feet",
  "result": 32.8084
}


Other examples:

GET  http://localhost:5197/api/convert?category=weight&from=kilograms&to=pounds&value=10

GET  http://localhost:5197/api/convert?category=temperature&from=celsius&to=fahrenheit&value=25


Prerequisites

Make sure you have the .NET 10 SDK installed.

Verify your installation:

dotnet --version

Running Locally

Clone the repository:

git clone <your-repository-url>


Navigate to the project:

cd UnitConverterApi\Unit.Converter


Restore the project:

dotnet restore


Build the project:

dotnet build


Run the API:

dotnet run


Once the application starts, the terminal will display the local URLs.

Localhost

The API can be accessed locally at:

 http://localhost:5197


Example API request:

 http://localhost:5197/api/convert?category=length&from=meters&to=feet&value=10


If your launchSettings.json configures a different port, use the URL shown in the terminal after running dotnet run.

Project Structure
UnitConverterApi/
│
├── Unit.Converter/
│   ├── Properties/
│   │   └── launchSettings.json
│   │
│   ├── Endpoints/
│   │   └── ...
│   │
│   ├── Models/
│   │   └── ...
│   │
│   ├── Services/
│   │   └── ...
│   │
│   ├── Program.cs
│   └── Unit.Converter.csproj
│
├── .gitignore
└── README.md

Design Decisions
RESTful API

The application is implemented as an HTTP REST API rather than a server-rendered web application. This allows different clients, such as web applications, mobile applications, or other services, to consume the conversion functionality.

Conversion Categories

Conversions are organized by category:

length
weight
temperature


This keeps the API consistent and makes it straightforward to add new categories later.

Hardcoded Conversion Data

Conversion factors are currently stored in the application rather than a database.

This follows the requirements of the challenge and keeps the solution simple. Since conversion definitions are relatively static, introducing a database at this stage would add unnecessary complexity.

Extensibility

The application is designed with future expansion in mind. The current implementation supports a limited number of units, but the conversion logic can be extended without changing the fundamental API contract.

A future version could move unit definitions into configuration or a database to support hundreds of units and conversion types.

Temperature Conversions

Temperature conversion is handled separately from simple multiplication-based conversions because Celsius, Fahrenheit, and Kelvin require offsets in addition to scaling factors.

Validation

The API validates the requested conversion category, source unit, target unit, and numerical value. Invalid requests return an appropriate HTTP error response rather than attempting an invalid conversion.

Technical Stack
C#
ASP.NET Core Minimal API
.NET 10
RESTful HTTP API
No external NuGet packages required
Future Improvements

Potential improvements for a production-ready version include:

Add more unit categories such as volume, area, speed, time, and data
Move unit definitions to configuration or a database
Add comprehensive automated tests
Add API versioning
Add structured logging
Add centralized exception handling
Add authentication and authorization if required
Add CI/CD using GitHub Actions
Add containerization with Docker
Add API documentation and interactive Swagger/OpenAPI support
Original Challenge

This project was developed as part of the Unit Converter project.

The implementation has been adapted to meet the requirements of the Unit Conversion API technical challenge.
