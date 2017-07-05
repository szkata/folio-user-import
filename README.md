# User import module for FOLIO

## Configuration

You can set the configuration values with npm config 
e.g. npm config set folio-bulk-user-import:FOLIO_PORT 9130

Every setting has a default fallback value.

### FOLIO configuration options
    FOLIO_HOST - Hostname of OKAPI
    FOLIO_PORT - Port of OKAPI
    FOLIO_PROTOCOL - Protocol of OKAPI
    FOLIO_TENANT - Tenant id
    FOLIO_USERNAME - Username for authentication
    FOLIO_PASSWORD - Password for username
    FOLIO_FILENAME - File name with user data
    FOLIO_PAGESIZE - Number of users to search for in one query
    FOLIO_LOGFILE - Log file for user import

## Usage

Use module in a script

    var bulk-import = require('folio-bulk-user-import');
    bulk-import();

optional parameter: user data file name

Run code locally
    cd into directory
    npm install
    npm start

## How it works?

1. Login to FOLIO with credentials set in the configuration values.
2. Get list of address types.
3. Get list of patron groups.
4. Read user data from the configured JSON file.
5. Query FOLIO if users already exist in the system (in batch of FOLIO_PAGESIZE number of users)
6. Decide by the result of the query if the current user have to be inserted or updated in the system.
7. Update existing users.
8. Create non-existing users.