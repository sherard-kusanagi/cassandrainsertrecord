---
title: CassandraDB Insert Activity
---

# CassandraDB Insert Activity
This activity allows you to Insert a record to a particular table from the CassandraDB server

## Installation
### Flogo CLI
```bash
flogo install github.com/sherard-kusanagi/cassandrainsertrecord
```

## Schema
Inputs and Outputs:

```json
{   
  "inputs":[
    {
      "name": "ClusterIP",
      "type": "string",
	  "required": true      
    },
	 {
      "name": "ClusterPort",
      "type": "integer",
	  "required": true      
    },
	{
      "name": "Keyspace",
      "type": "string",
      "required": true
    },
	{
      "name": "TableName",
      "type": "string",
      "required": true
    },
	 {
      "name": "InsertQuery",
      "type": "string",
      "required": true
    }
  ],
  "outputs": [
    {
      "name": "result",
      "type": "any"
    }
  ]
 }
```
## Settings
| Setting        | Required | Description |
|:---------------|:---------|:------------|
| ClusterIP      | True     | The CassandraDB cluster instance |
| ClusterPort    | True     | The CassandraDB Port instance. Default 9042|              
| Keyspace       | True     | The name of the Keyspace
| TableName      | True     | The name of table to delete record
| InsertQuery    | True		| The insert query is to insert a record into the table|

## Example
The below example is to insert a record into CassandraDB

```json
{
  "id": "CassandraDB_1",
  "name": "CassandraDB connector",
  "description": "Insert record into CassandraDB",
  "activity": {
    "ref": "github.com/sherard-kusanagi/cassandrainsertrecord",
    "input": {
      "ClusterIP": "127.0.0.1",
	  "ClusterPort": 9042,
      "Keyspace": "sample",
      "TableName": "employee",
	  "InsertQuery": "INSERT INTO employee (empid , name, salary) VALUES (102, 'xyz', 5005)"          
    }
  }
}
```