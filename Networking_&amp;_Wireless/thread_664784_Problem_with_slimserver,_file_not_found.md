---
title: "Problem with slimserver, file not found?"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by BeastlyKings on 2008-01-11
Can I please get some help with slimserver? I installed it, but when I try running it I get this error:

```
tom@tom-desktop:~$ slimserver
2008-01-11 14:54:07.5124 ERROR: MySQLHelper: createSystemTables() Couldn't connect to database: [Can't connect to local MySQL server through socket '/home/tom/Cache/slimserver-mysql.sock' (2)]

tom@tom-desktop:~$ 

```


Help?

Edit:
I check my error log and found this:
"080111 17:04:40  InnoDB: Started; log sequence number 0 43655
080111 17:04:40 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
080111 17:04:40 [ERROR] Do you already have another mysqld server running on port: 9092 ?
080111 17:04:40 [ERROR] Aborting

080111 17:04:40  InnoDB: Starting shutdown...
080111 17:04:42  InnoDB: Shutdown completed; log sequence number 0 43655
080111 17:04:42 [Note] /usr/sbin/mysqld: Shutdown complete"


SO I thought to myself, port 9092?
So then i checked my.cnf and the default port was set to 9092, I changed it but got the same result.
Then I check my.cnf file in /ect, and IT was set to 3306.


I could REALLY use some help.

---

### Post by BeastlyKings on 2008-01-15
Well apparently slimserver was already running, while still getting there error I could go to [http://localhost:9000](http://localhost:9000) and control/play my music through my chumby, so yeah I guess it works now, I've still got other problems like it no recognizing my music folder.. at all. but I guess..

---

