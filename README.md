# Call REST API programmatically and generate a CSV file
Repository for create for create csv file and store data inside.
- fetch data using meusem api.
- store this data into csv file .
- use csvjson package for convert json data to csv.
- And use fs package for read and write file.
- first fetch data from meuseum api then create new file readwriteCSV.js.
- install both package and then import in this file .
- install
```
npm i csvjson fs
```
- import
```
const csvjson = require('csvjson')
const fs = require('fs')
const readFile = fs.readFile;
const writeFile = fs.writeFile;
```
- then first read json data file using readstrim for fs.
```
// Reading json file(filename -data.json)
readFile('./data.json', 'utf-8', (err, fileContent) => {
    if (err) {
        // Doing something to handle the error or just throw it
        logger.error(err); 
        throw new Error(err);
    }
    })
  ```
- then convert this json data to csv using jsoncsv package.
```
// Convert json to csv function
    const csvData = csvjson.toCSV(fileContent, {
        headers: [{id:'key',title:'key'}]
    });
 ```
- then store this converted data to csv file using write strem for fs.
```
// Write data into csv file named college_data.csv
    writeFile('data.csv', csvData, (err) => {
        if(err) {
            // Do something to handle the error or just throw it
            logger.error(err); 
            throw new Error(err);
        }
        logger.info(`Data stored into ${'./data.csv'} successfully`);
    });
 ```
- make sure your covert and write both function write inside the read function like you can see inside this src folder readwriteCSV.js .
- after that run script on terminal
```
node readwriteCSV.js
```
- If all working well then you got the successful msg and also in your project directry created new csv file.
