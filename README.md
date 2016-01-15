# anathema-data
Data for Walking River's Anathema mobile game (coming soon).

## How it works
At start-up, the app detects whether or not there is an internet connection.
If so, data.json is downloaded from the web server, passing an "If-None-Match" header
with the eTag value from last time the file was download (or none if this is the first time).

If the data.json file has not changed, we will get an HTTP 304-Not Modified. At that point,
the application can continue.

If we receive an HTTP 200-OK response, this means the data.json file has changed since the 
last time the application checked. In this case, the application will update its internal database
with the contents of data.json, and then proceed to download the files referenced.

Each file to be downloaded will go through similar logic.
 
 