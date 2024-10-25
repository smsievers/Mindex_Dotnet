# 10/25/24: From Seth
   -First and foremost: thank you for the opportunity. My interview experience with Mindex has been great so far, and I have felt very welcomed and respected. This is not always the case in the modern hiring environment, and I can't tell you enough how much it means to me.

   -This code challenge was a lot of fun, and I really enjoyed working on it. The tasks themselves were fairly simple, but gave me a great chance to work on some stuff that I don't often get to touch or have only recently started using (EFCore and Inmemory Dbs, specifically). I did my best to follow what I saw to be the conventions laid out in both the main and test projects while still sticking at least somewhat to the 'style' of code that I am used to writing and naturally fall into.

Please feel to reach out to me at seth_sievers@yahoo.com if you have any questions or would like to chat.

## Documentation on new additions
   -I opted mostly to document code via comments inline, so I won't have much to write here besides drawing attention to exactly what it is I created.

### New stuff:
   -New Compensation and ReportingStructure models
   -A new Compensation Controller/Service/Repository, complete with CreateCompensation and GetCompensationByEmployeeId endpoints and their associated service/repo methods
   -A new GetReportingStructureById endpoint in the employee controller, along with associated Service and Repo methods. I opted not to have a separate Controller/Service/Repo
    for this method, as it did not persist any new data. I recognize that this is a philosophical choice, and would probably end up moving it eventually as functionality expands
    in this "application"
   -Logic in the dataseeder to populate some minimal compensation data for your testing ease (this comes with the data file).
   -Test coverage for every new endpoint in the test project. I opted to follow the convention established for the previously existing endpoints, and did not deviate too much from them. These tests were run using VS's test explorer.


# Mindex Coding Challenge
## What's Provided
A simple [.Net 6](https://dotnet.microsoft.com/en-us/download/dotnet/6.0) web application has been created and bootstrapped
with data. The application contains information about all employees at a company. On application start-up, an in-memory
database is bootstrapped with a serialized snapshot of the database. While the application runs, the data may be
accessed and mutated in the database without impacting the snapshot.

### How to Run
You can run this by executing `dotnet run` on the command line or in [Visual Studio Community Edition](https://www.visualstudio.com/downloads/).


### How to Use
The following endpoints are available to use:
```
* CREATE
    * HTTP Method: POST
    * URL: localhost:8080/api/employee
    * PAYLOAD: Employee
    * RESPONSE: Employee
* READ
    * HTTP Method: GET
    * URL: localhost:8080/api/employee/{id}
    * RESPONSE: Employee
* UPDATE
    * HTTP Method: PUT
    * URL: localhost:8080/api/employee/{id}
    * PAYLOAD: Employee
    * RESPONSE: Employee
```
The Employee has a JSON schema of:
```json
{
  "type":"Employee",
  "properties": {
    "employeeId": {
      "type": "string"
    },
    "firstName": {
      "type": "string"
    },
    "lastName": {
          "type": "string"
    },
    "position": {
          "type": "string"
    },
    "department": {
          "type": "string"
    },
    "directReports": {
      "type": "array",
      "items" : "string"
    }
  }
}
```
For all endpoints that require an "id" in the URL, this is the "employeeId" field.

## What to Implement
Clone or download the repository, do not fork it.

### Task 1
Create a new type, ReportingStructure, that has two properties: employee and numberOfReports.

For the field "numberOfReports", this should equal the total number of reports under a given employee. The number of
reports is determined to be the number of directReports for an employee and all of their direct reports. For example,
given the following employee structure:
```
                    John Lennon
                /               \
         Paul McCartney         Ringo Starr
                               /        \
                          Pete Best     George Harrison
```
The numberOfReports for employee John Lennon (employeeId: 16a596ae-edd3-4847-99fe-c4518e82c86f) would be equal to 4.

This new type should have a new REST endpoint created for it. This new endpoint should accept an employeeId and return
the fully filled out ReportingStructure for the specified employeeId. The values should be computed on the fly and will
not be persisted.

### Task 2
Create a new type, Compensation. A Compensation has the following fields: employee, salary, and effectiveDate. Create
two new Compensation REST endpoints. One to create and one to read by employeeId. These should persist and query the
Compensation from the persistence layer.

## Delivery
Please upload your results to a publicly accessible Git repo. Free ones are provided by Github and Bitbucket.#   M i n d e x _ D o t n e t 
 
 
