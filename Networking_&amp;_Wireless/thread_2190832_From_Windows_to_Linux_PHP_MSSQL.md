---
title: "From Windows to Linux PHP MSSQL"
date: 2013-11-29
forum: Networking &amp; Wireless
---

### Post by scarabeuz2 on 2013-11-29
Hi community,

i want to move my PHP application from Windows to Linux.
I'm now doing try and error since 7 days and need a solution soon.. so I need do my first linux-related post. I followed many guides (searched on google) ..

The Application before ran on Windows 2008 R2 With PHP 5.4 and external MSSQL 2012 database server, setted up ODBC and running via odbc_connect() function without problems.
Now I try to do the same from ubuntu. I started developing on a test server that is completely installed and configured like the productive server.

Using the testserver everything is running well (using mssql_connect, FreeTDS).

My /etc/freetds/freetds.conf
```
[global]        # TDS protocol version
        tds version =  7.0


        # Whether to write a TDSDUMP file for diagnostic purposes
        # (setting this to /tmp is insecure on a multi-user system)
        dump file = /tmp/freetds.log
#       debug flags = 0xffff


        # Command and connection timeouts
        timeout = 10
        connect timeout = 10


        # If you get out-of-memory errors, it may mean that your client
        # is trying to allocate a huge buffer for a TEXT field.
        # Try setting 'text size' to a more reasonable limit
        text size = 64512
        client charset = UTF-8
# A typical Sybase server
[egServer50]
        host = symachine.domain.com
        port = 5000
        tds version = 5.0


# A typical Microsoft server
[TEST]
        host = test.example.org
        instance = INSTANCE
        tds version = 8.0
[PRODUCTIVE]
        host = db.example.org
        port = 1433



```
First I configured PRODUCTIVE same as TEST but it failed to get an instance port so i specified the port.
I tried everything such as adding tds version, charset, etc.. after each change i checked /tmp/freetds.log 

```
config.c:301:Success: [PRODUCTIVE] defined in /etc/freetds/freetds.conf.iconv.c:330:tds_iconv_open(0x7f1f97ed9ae0, UTF-8)
iconv.c:349:setting up conversions for client charset "UTF-8"
iconv.c:351:preparing iconv for "UTF-8" <-> "UCS-2LE" conversion
iconv.c:391:preparing iconv for "ISO-8859-1" <-> "UCS-2LE" conversion
iconv.c:394:tds_iconv_open: done
net.c:205:Connecting to 123.123.123.123 port 1433 (TDS version 7.0)
net.c:270:tds_open_socket: connect(2) returned "Operation now in progress"
net.c:316:tds_open_socket() failed
util.c:331:tdserror(0x7f1f97d994d0, 0x7f1f97ed9ae0, 20009, 115)
dblib.c:7929:dbperror(0x7f1f97ed1fd0, 20009, 115)
dblib.c:7981:20009: "Unable to connect: Adaptive Server is unavailable or does not exist"
dblib.c:8002:"Unable to connect: Adaptive Server is unavailable or does not exist", client returns 2 (INT_CANCEL)
util.c:361:tdserror: client library returned TDS_INT_CANCEL(2)
util.c:384:tdserror: returning TDS_INT_CANCEL(2)
dblib.c:1443:dbclose(0x7f1f97ed1fd0)
dblib.c:258:dblib_del_connection(0x7f1f8cf65840, 0x7f1f97ed9ae0)
mem.c:615:tds_free_all_results()
dblib.c:305:dblib_release_tds_ctx(1)
dblib.c:5882:dbfreebuf(0x7f1f97ed1fd0)
dblib.c:739:dbloginfree(0x7f1f97eb5e80)

```

```
**Warning: mssql_connect(): Unable to connect to server**
```

Same using sqsh to connect
```
# sqsh -S TEST -U user -P passsqsh-2.1.7 Copyright (C) 1995-2001 Scott C. Gray
Portions Copyright (C) 2004-2010 Michael Peppler
This is free software with ABSOLUTELY NO WARRANTY
For more information type '\warranty'
1>

```
connected without problems..

```
~# sqsh -S PRODUCTIVE -U user -P passsqsh-2.1.7 Copyright (C) 1995-2001 Scott C. Gray
Portions Copyright (C) 2004-2010 Michael Peppler
This is free software with ABSOLUTELY NO WARRANTY
For more information type '\warranty'
Open Client Message
Layer 0, Origin 0, Severity 78, Number 41
Unable to connect: Adaptive Server is unavailable or does not exist

```

First time I thought firewall problem or something like that so I tried to connect to it basiccally
```
nmap -p 1433 db.example.org

Starting Nmap 6.40 ( http://nmap.org ) at 2013-11-29 17:57 UTC
Nmap scan report for db.example.org (123.123.123.123)
Host is up (0.16s latency).
PORT     STATE    SERVICE
1433/tcp filtered ms-sql-s


Nmap done: 1 IP address (1 host up) scanned in 2.03 seconds

```

So service is up and waiting for me to solve this problem -.-
I also tried to connect to the db using other php merhods like PDO (dblib and ODBC), odbc_connect. Same problem there.

I would really love you if you give me a hint or sth that gets me to solve this problem

---

