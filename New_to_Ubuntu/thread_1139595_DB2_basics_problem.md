---
title: "DB2 basics problem"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by resander on 2009-04-27
I have just downloaded and installed DB2 Express 9.5 on Ubuntu 8.10. 

First tried to create the sample database by:

ken@ken-desktop:~/sqllib/bin$ ./db2sampl

Starting the DB2 instance...
Creating database "SAMPLE"...
Attempt to create the database "SAMPLE" failed.
SQL1032N No start database manager command was issued. SQLSTATE=57019
'db2sampl' processing complete.

so I thought that I had to start the db manually. I did not know how to but tried:

ken@ken-desktop:~/sqllib/bin$ db2start
SQL1220N The database manager shared memory set cannot be allocated.
ken@ken-desktop:~/sqllib/bin$

I don't know what this means.
Does anyone know how to start DB2? or has anyone actually successfully used DB2 on Ubuntu?

Hints would be most welcome.

---

### Post by jashwanthkc on 2009-08-26
just login with instance owner authority and issue db2start command then db2instance will start

---

