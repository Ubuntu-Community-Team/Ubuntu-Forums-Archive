---
title: "SQL Server error '80004005'"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by mlnease on 2009-05-09
Hello,

I tried to log onto an online database and received the following error message:

Microsoft OLE DB Provider for SQL Server error '80004005'

[DBNETLIB][ConnectionOpen (Connect()).]SQL Server does not exist or access denied.

/apply/send.asp, line 110 

I gather that this means I'm unable to log on to a SQL OBDC database.  I thought it might help to install unixodbc-bin but I did and it didn't.

Any suggestions?

Thanks,

mike

---

### Post by Didius Falco on 2009-05-09
> **mlnease said:**
> Hello,

I tried to log onto an online database and received the following error message:

Microsoft OLE DB Provider for SQL Server error '80004005'

[DBNETLIB][ConnectionOpen (Connect()).]SQL Server does not exist or access denied.

/apply/send.asp, line 110 

I gather that this means I'm unable to log on to a SQL OBDC database.  I thought it might help to install unixodbc-bin but I did and it didn't.

Any suggestions?

Thanks,

mike

Have you looked at line 110 of /apply/send.asp - it sounds like that is what the eror is pointing to.

Here are some possible paths to an answer.

This website defines the problem in less technical terms:

[http://tutorials.aspfaq.com/8000xxxxx-errors/80004005-errors.html](http://tutorials.aspfaq.com/8000xxxxx-errors/80004005-errors.html)

It then points to several pages with potetntial solutions.

I hope it helps.


Regards,

Didius

---

### Post by mlnease on 2009-05-09
> **Didius Falco said:**
> Have you looked at line 110 of /apply/send.asp - it sounds like that is what the eror is pointing to.

Here are some possible paths to an answer.

This website defines the problem in less technical terms:

[http://tutorials.aspfaq.com/8000xxxxx-errors/80004005-errors.html](http://tutorials.aspfaq.com/8000xxxxx-errors/80004005-errors.html)

It then points to several pages with potential solutions.

I hope it helps.


Regards,

Didius

Hi Didius,

And thanks for the quick response.  I've been looking at the 'less technical terms' and am for the moment somewhat mind-boggled.  I'll continue to look though, and post my solution if I can work it out.

mike

---

### Post by anewguy on 2009-05-09
The following is the section of the link that pertains to your error:

 
Microsoft OLE DB Provider for ODBC Drivers error '80004005' 
[Microsoft][ODBC SQL Server Driver][DBNMPNTW] ConnectionOpen(CreateFile()). 
 
or 
 
Microsoft OLE DB Provider for ODBC Drivers error '80004005' 
[Microsoft][ODBC SQL Server Driver][TCP/IP Sockets] SQL Server does not exist or access denied. 
 
or 
 
Microsoft OLE DB Provider for SQL Server error '80004005'  
[DBNETLIB][ConnectionOpen (Connect()).] SQL Server does not exist or access denied.  
 
or 
 
 
Microsoft OLE DB Provider for ODBC Drivers error '80004005'  
[Microsoft][ODBC SQL Server Driver][Named Pipes] Specified SQL server not found.  
 
or 
 
Microsoft OLE DB Provider for ODBC Drivers error '80004005' 
[Microsoft][ODBC SQL Server Driver] Client unable to establish connection.
 
While the first error message is definitely more cryptic than the others, they all mean the same thing. The first simply uses DBNMPNTW, which is the protocol name for named pipes. What the error means is that the SQL Server you defined in your connection string is invalid - either because it is currently down, you named it wrong (either by hostname, DNS/domain or IP address), or you don't have permission to connect. 
 
If you are expecting to connect by IP address, make sure you override named pipes (see Article #2082).  
 
If you are using SQL Server authentication, make sure both ends are set up for it (see Article #2138).  
 
If the error is 'SQL Server does not exist or access denied', see KB #328306, which has a large variety of possible causes and solutions. Also see KB #888228 if you are trying to connect to a named instance within a SQL Server 2000 cluster. 
 
If the ASP page and SQL Server are on the same machine, then it may be a loopback problem - try using 127.0.0.1, LOCALHOST, (local), or just a period (instead of the external IP or network name) in the connection string. 
 

Since this is an onine database, not something local, it would appear that either the name you specified for the database is incorrect, the userid/password for logging into the database is incorrect.  There may be something else, and I sure don't claim to be an expert on this at all.  Just from the outside looking in, that would be my suspicion.

Have you connected to this database before?  How are you asking for the access?

Dave :)

---

### Post by mlnease on 2009-05-09
> **anewguy said:**
> 
Have you connected to this database before?  How are you asking for the access?

Dave :)

Hi Dave,

Wow--a lotta info.  I'll review what I haven't quoted here and let you know if I come up with anything.

No, I haven't connected before; and I connected via a link on their website.  I've requested help from their webmaster and will post any response here if it seems pertinent.

Thanks for your time.

mike

---

