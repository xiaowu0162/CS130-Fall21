# Application API Documentation
In this document, we describe the APIs of the application in detail. Our working API consists of two parts: the communication REST API between frontend and backend ([Server](#Server)), and the data passing API between the backend and the Database ([Database](#Database)). The API for the Database is automatically generated by JSDoc, and the API for the Server is written in a similar style since the Server does not use object-oriented programming. 

<a name="Database"></a>

## Database
Class wrapping database operations.

**Kind**: global class  

* [Database](#Database)
    * [.connect(url)](#Database.connect)
    * [.db(dbName)](#Database.db) ⇒ <code>database</code>
    * [.close()](#Database.close)
    * [.store_user(body)](#Database.store_user)
    * [.read_user(username)](#Database.read_user) ⇒ <code>User</code>
    * [.read_activeHubs()](#Database.read_activeHubs) ⇒ <code>Array.&lt;Hub&gt;</code>
    * [.read_nearbyHubs(loc, radius)](#Database.read_nearbyHubs) ⇒ <code>Array.&lt;Hub&gt;</code>
    * [.read_hub(hubId)](#Database.read_hub) ⇒ <code>Hub</code>
    * [.store_hub(body)](#Database.store_hub)
    * [.schedule_jobs()](#Database.schedule_jobs)
    * [.read_assignedJobs(username)](#Database.read_assignedJobs) ⇒ <code>Array.&lt;Job&gt;</code>
    * [.read_job(jobId)](#Database.read_job) ⇒ <code>Job</code>
    * [.store_job(body)](#Database.store_job)
    * [.read_maxMaxJobId()](#Database.read_maxMaxJobId) ⇒ <code>number</code>
    * [.read_maxMaxHubId()](#Database.read_maxMaxHubId) ⇒ <code>number</code>

<a name="Database.connect"></a>

### Database.connect(url)
Connect the database

**Kind**: static method of [<code>Database</code>](#Database)  

| Param | Type | Description |
| --- | --- | --- |
| url | <code>string</code> | The url for the database |

<a name="Database.db"></a>

### Database.db(dbName) ⇒ <code>database</code>
Database wrapper

**Kind**: static method of [<code>Database</code>](#Database)  
**Returns**: <code>database</code> - - Database for MongoDB operations.  

| Param | Type | Description |
| --- | --- | --- |
| dbName | <code>string</code> | Name of the database. |

<a name="Database.close"></a>

### Database.close()
Close the connection

**Kind**: static method of [<code>Database</code>](#Database)  
<a name="Database.store_user"></a>

### Database.store\_user(body)
Stores a user

**Kind**: static method of [<code>Database</code>](#Database)  

| Param | Type | Description |
| --- | --- | --- |
| body | <code>User</code> | JSON of a user file. |

<a name="Database.read_user"></a>

### Database.read\_user(username) ⇒ <code>User</code>
Reads a user

**Kind**: static method of [<code>Database</code>](#Database)  
**Returns**: <code>User</code> - - JSON of the requested user file.  

| Param | Type | Description |
| --- | --- | --- |
| username | <code>string</code> | Username of the requested user. |

<a name="Database.read_activeHubs"></a>

### Database.read\_activeHubs() ⇒ <code>Array.&lt;Hub&gt;</code>
Returns all currently active hubs.

**Kind**: static method of [<code>Database</code>](#Database)  
**Returns**: <code>Array.&lt;Hub&gt;</code> - - Array of JSON of currently active hubs.  
<a name="Database.read_nearbyHubs"></a>

### Database.read\_nearbyHubs(loc, radius) ⇒ <code>Array.&lt;Hub&gt;</code>
Reads nearby hubs

**Kind**: static method of [<code>Database</code>](#Database)  
**Returns**: <code>Array.&lt;Hub&gt;</code> - - Array of JSON of hubs satisfying the query.  

| Param | Type | Description |
| --- | --- | --- |
| loc | <code>coordinates</code> | Cordinates of the center of the search. |
| radius | <code>number</code> | Radius of the search in miles. |

<a name="Database.read_hub"></a>

### Database.read\_hub(hubId) ⇒ <code>Hub</code>
Reads a hub

**Kind**: static method of [<code>Database</code>](#Database)  
**Returns**: <code>Hub</code> - - JSON of the requested hub.  

| Param | Type | Description |
| --- | --- | --- |
| hubId | <code>number</code> | ID of the requested hub. |

<a name="Database.store_hub"></a>

### Database.store\_hub(body)
Stores a hub

**Kind**: static method of [<code>Database</code>](#Database)  

| Param | Type | Description |
| --- | --- | --- |
| body | <code>Hub</code> | JSON of a hub file. |

<a name="Database.schedule_jobs"></a>

### Database.schedule\_jobs()
Schedule unassigned jobs that are within 1 hr from scheduled time.

**Kind**: static method of [<code>Database</code>](#Database)  
<a name="Database.read_assignedJobs"></a>

### Database.read\_assignedJobs(username) ⇒ <code>Array.&lt;Job&gt;</code>
Reads jobs assigned to a driver and assign jobs using schedule_jobs.

**Kind**: static method of [<code>Database</code>](#Database)  
**Returns**: <code>Array.&lt;Job&gt;</code> - - Array of JSON of jobs assigned to the driver.  

| Param | Type | Description |
| --- | --- | --- |
| username | <code>string</code> | Username of the requested driver. |

<a name="Database.read_job"></a>

### Database.read\_job(jobId) ⇒ <code>Job</code>
Reads a job and assign jobs using schedule_jobs.

**Kind**: static method of [<code>Database</code>](#Database)  
**Returns**: <code>Job</code> - - JSON of the requested job.  

| Param | Type | Description |
| --- | --- | --- |
| jobId | <code>number</code> | ID of the requested job. |

<a name="Database.store_job"></a>

### Database.store\_job(body)
Stores a job

**Kind**: static method of [<code>Database</code>](#Database)  

| Param | Type | Description |
| --- | --- | --- |
| body | <code>Job</code> | JSON of a job file. |

<a name="Database.read_maxMaxJobId"></a>

### Database.read\_maxMaxJobId() ⇒ <code>number</code>
Reads the currect maximum jobId

**Kind**: static method of [<code>Database</code>](#Database)  
**Returns**: <code>number</code> - - Currect maximum jobId.  
<a name="Database.read_maxMaxHubId"></a>

### Database.read\_maxMaxHubId() ⇒ <code>number</code>
Reads the currect maximum hubId

**Kind**: static method of [<code>Database</code>](#Database)  
**Returns**: <code>number</code> - - Currect maximum hubId.  

<a name="Server"></a>

## Server
The Backend. 
* [Server](#Server)
    * [GET /login](#Server.getLogin)
    * [POST /login](#Server.postLogin)
    * [GET /api/hubs](#Server.getAPIHubs) ⇒ <code>Array.&lt;Hub&gt;</code>
    * [POST /api/hubs](#Server.postAPIHubs) ⇒ <code>Hub</code>
    * [GET /api/jobs](#Server.getAPIJobs) ⇒ <code>Array.&lt;Job&gt;</code>
    * [POST /api/jobs](#Server.postAPIJobs) ⇒ <code>Job</code>

<a name="Server.getLogin"></a>

### GET /login()
Returns an HTML page containing an HTML form with three input elements: username, usertype, and password. When the user presses the submit button, the page should issue a request <code>POST /login</code> with <code>username=:username&usertype=:usertype&password=:password</code> in the body.

**Kind**: static method of [<code>Server</code>](#Server)  

<a name="Server.postLogin"></a>

### POST /login(username, usertype, password)
Checks that the provided username, usertype, and password matches the record. If the provided information does not match, returns 401 return code. Otherwise, set an authorization session cookie and return 200.

**Kind**: static method of [<code>Server</code>](#Server)  

| Param | Type | Description |
| --- | --- | --- |
| username | <code>string</code> | User name |
| usertype | <code>string</code> | "user" or "driver" |
| password | <code>string</code> | Password |

<a name="Server.getAPIHubs"></a>

### GET /api/hubs(hubid=null, long=null, lat=null, rad=null) ⇒ <code>Array.&lt;Hub&gt;</code>
Returns the information of the requested hub(s). If hubid is <code>null</code>, return all the active hubs in the database. 
If long, lat, and rad are also given, only return active hubs that are in the circle centered at (long, lat) with 
radius rad. 

**Kind**: static method of [<code>Server</code>](#Server)  

**Returns**: <code>Array.&lt;Hub&gt;</code> - - Array of JSON of hubs  

| Param | Type | Description |
| --- | --- | --- |
| hubid | <code>number</code> | The unique hub id | 
| long | <code>number</code> | A number specifying the longitude of the center of search range | 
| lat | <code>number</code> | A number specifying the latitude of the center of search range | 
| rad | <code>number</code> | A number specifying the circle of search range | 

<a name="Server.postAPIHubs"></a>  

### POST /api/hubs(hubId, description, startTime, endTime, location=null) ⇒ <code>Hub</code>
Create or update a hub entry. If hubId is 0, insert a new hub and return 201. If hubId> 0 and hubIdrecord exists, 
update the existing hub entry by overwriting the description, location, startTime, endTime fields in the request. Return 200.
Otherwise, return 404.

**Kind**: static method of [<code>Server</code>](#Server) 

**Returns**: <code>Hub</code> - - The updated or created Hub

| Param | Type | Description |
| --- | --- | --- |
| hubid | <code>number</code> | The unique hub id | 
| description | <code>string</code> | Description of the hub |
| startTime | <code>startTime</code> | When the hub starts | 
| endTime | <code>endTime</code> | When the hub ends | 
| location | <code>array</code> | Longitude and Latitude of the hub (can be null) |

<a name="Server.getAPIJobs"></a> 

### GET /api/jobs(username=null, jobid=null) ⇒ <code>Array.&lt;Job&gt;</code>
Get all the jobs associated with username or jobid. If username or jobid does not exist, return 404.
If jobid is not null, return the job corresponding to the jobid. 
If username exists and correspond to a driver, return a JSON containing a sorted list of jobs.
If username exists and correspond to a customer, return a JSON containing a single job.

**Kind**: static method of [<code>Server</code>](#Server) 

**Returns**: <code>Array.&lt;Job&gt;</code> - - Array of JSON of jobs  

| Param | Type | Description |
| --- | --- | --- |
| username | <code>string</code> | User name |
| jobid | <code>number</code> | The unique job id | 

<a name="Server.postAPIJobs"></a> 

### POST /api/jobs(data) ⇒ <code>Job</code>
Create a new job or update an existing job. First construct a Job object using the data given. 
If the jobId is 0, create a new job and add it to the database and return the job with code 201.
Otherwise, update the status of an existing job and return the hub with code 200. 
If the jobId is not 0 and the job is not found, return 400.

**Kind**: static method of [<code>Server</code>](#Server) 

**Returns**: <code>Job</code> - - The updated or created job

| Param | Type | Description |
| --- | --- | --- |
| data | <code>JSON</code> | The data corresponding to a new job or an existing job. |
