# Data Modeling with Apache Cassandra
_________
Sparkify, a startup, wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. Their data is in  in a directory of CSV files on user activity on the app.
The goal of this project is to build a data model in Cassandra Keyspace using python that allow analytics team to optimize specific queries that is important to business.

## DataSet
![Imgur Image](https://github.com/xchen715/Data_Engineering/blob/master/Data_Modeling_with_Apache_Cassandra/images/image_event_datafile_new.jpg)

## Goals/Queries to Be Optimized
____________
### Goal 1. Get the song information of specific item in specific session.
**Example query:** `SELECT artist, song, length FROM session_library WHERE sessionId = 338 AND itemInSession = 4`
 
### Goal 2. Get songs information order by listening sequence for a specific user during a specific session.
**Example query:** `SELECT artist, song, firstName, lastName FROM user_library WHERE userId = 10 AND sessionId =182` 

### Goal 3. Who listen to specific song.
**Example query:** `SELECT firstName, lastName FROM song_library WHERE song = 'All Hands Against His Own'` 

## Table Structure
_____________

**1. session_library:**
- Partition Key: *sessionId*
- Clustering Columns: *itemInsession*

**2. user_library:**
- Partition Key: *userId, sessionId*
- Clustering Columns: *itemInsession*

**3. song_library:**
- Partition Key: *song*
