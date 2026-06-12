---
title: "WINE - ODBC - MSSQL Server"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by sarves on 2010-07-15
I have a windows application running on WINE and that application need to be connected to a MSSQL SServer that is running separately.

When I try to set up the ODBC connection it says :

Connection failed:
SQLState : '01000'
SQL Server Error : 10061
.................
Connection failed :
SQLState : '08001'
SQL Server Error : 17
.............

what could be the issue?

Sarves

---

### Post by gr4nf on 2010-07-15
You could have any number of problems here, I think. I've heard that MSSQL Server does not allow remote connections by default, so see if you can find any settings like that on the server side. On the client side, I would check the wine application database:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

for any information regarding the program you are using to see if others have had a similar issue.

You should also remember to check for simple errors, like getting the user name and password for the server correct (although this would probably give a connection refused error, not the one you got.)

Try pinging your server from the client.

---

### Post by sarves on 2010-07-15
I have few other windows machines connected to the same database. Therefore it is not about making remote connections. 

I also tried winhq forum and stil no luck

Sarves

---

### Post by gr4nf on 2010-07-15
I'm assuming you have a connection to the internet from your ubuntu box? Also, if you ping the IP of your SQL server from it, can you get the connection? Thirdly, is your ubuntu machine on the same LAN as the SQL server?

---

### Post by sarves on 2010-07-15
Yes for all..
Ubuntu has internet connection and the machine and the MS SQL Server are in the same network. I could ping from the Ubuntu box.

Sarves

---

