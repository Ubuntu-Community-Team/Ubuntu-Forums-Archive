---
title: "Ubuntu Firebird SQL CLI  (Command Line Interface)"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Don Bowen on 2010-02-06
First of all, thanks to all the people who were kind enough (patient) to put up with all my begginner questions...
Here's another one...
I've just installed Firebird SQL (2.1 Super).  I've worked with it before under Windows, and I know that it has a command line utility called ISQL (Interactive SQL).  
I'm pretty sure that utility, as well as the other command line utilities, installed when I asked Synaptic to install the whole package for me.
They're there....somewhere...but the question now is ... where?
Windows programs installed to C:\Program Files
Where is the equivalent in Ubuntu?

---

### Post by mushwars on 2010-02-06
basically you can see the paths to binarys doing this

```
echo $PATH
```

you can locate a binary doing this
```
which <binary name>
```

if you dont know what the program is called you can find it using tab...

try typing fire <tab> <tab> that will show a list of all the binarys that start with fire.

If you think it starts with the name sql then sql <tab> <tab>

---

### Post by Don Bowen on 2010-02-06
sorry, should have looked first....  I found this, and it seems to answer most questions.

[http://www.firebirdsql.org/manual/ubusetup.html](http://www.firebirdsql.org/manual/ubusetup.html)

I'm still nervous about creating and opening a database in the ISQL CLI.  It's easy under windows, and as I recall, doesn't work at all under Linux... or at least I don't know how it works... so as soon as I get the ISQL CLI working, we'll try that one again!
It's the step that stopped me cold last time I fired up Ubuntu with Lazarus and Firebird.

---

### Post by Don Bowen on 2010-02-06
OK...it's coming back to me now... but the stuck place arrives in minutes this time and not days....

the CLI interface for Firebird may be found at 
/USR/BIN
you type ISQL-FD

to start the CLI running.  Now you can connect to a database in the usual way....
well NO, no you can't, and that's what killed this effort last time.

Under windows you would connect to the database as in the example used in the installing Firebird for Ubuntu tutorial I already referened.

the Firebird ISQL command is
SQL> connect "/var/lib/firebird/2.1/data/employee.fdb " user 'SYSDBA' password 'SYSDBApassword';

if you followed the unpacking instructions in the tutorial.  What the tutorial doesn't account for is the error I
get when I try to do that!

Statement failed, SQLCODE = -902
Unable to complete network request to host "localhost".
-Failed to establish a connection.
-Connection refused

I do understand the nature of the problem.  SQL was designed for quick access over IP connections....thus ,
I can't connect to this database because I haven't established a connection with 127.0.0.1... my own machine!
How to overcome that?  A few months ago , I had to give up to do another project... I return to the fight once more.
Any thoughts?

---

### Post by Don Bowen on 2010-02-06
in the tutorial for setting up firebird under ubuntu ([http://www.firebirdsql.org/manual/ubusetup.html](http://www.firebirdsql.org/manual/ubusetup.html)) it reads:

Now you can switch to the firebird user with the                    **su** command if required.             

SU command?  What is that?  How does one use it?  I know...I'll ask Mr. Google...

---

### Post by Don Bowen on 2010-02-06
OK...here's what I think I know...
the Firebird SQL server must be running as a process for any of this to work.  To set up your machine to run the Firebird SQL server automatically, you can....

# dpkg-reconfigure firebird2.1-super

this will prompt you for a new password for the "firebird" user and ask you 
if you want to run the Firebird SQL service at startup.... I do...so off we go.

Now that I know the service is running, I can drop into the ISQL-FB CLI

#ISQL-FB

SQL> create database '/media/Data1501/test.fdb' user 'sysdba' password 'masterkey';

Yes, I know that it's not secure to leave the sysdba user password as 'masterkey', but I need the simplicity while learning.

That command worked on my machine because I have a drive defined as "/media/Data1501".   It would be different on your machine...but the idea is the same.

Interestingly enough, I never had to form a connection between 127.0.0.1 and the firebird sql server.... even though it gave me that "couldn't connect" error earlier.  It makes sense that the firebird service would define that connection on its own, but if that's so, why did I get that "couldn't connect" error?   Doesn't matter....it's connecting now... 
Is writing all this down as I encounter it useful to anyone?  I hope so.  If nothing else, I will use it again when, in 6 months, I'm trying to do this again and forgetting everything I know today.

---

### Post by mushwars on 2010-02-06
are you sure sql is running?

/etc/init.d/firesql start (or whatever its called)

---

### Post by Don Bowen on 2010-02-07
> **mushwars said:**
> are you sure sql is running?

/etc/init.d/firesql start (or whatever its called)


I think so.  I am able to create a database, add a table, populate the table with data fields, insert new records into the database, and have the database show me the data.
The SQL command "commit" doesn't generate an error, and when I come back the next day, the data is still there.

SQL runs as a process in windows, so I presume something like that is going on for Ubuntu.

---

### Post by Don Bowen on 2010-02-07
Now the next step is to get Lazarus to open the SQL file I made in the Firebird CLI.
There is actually a "Firebird" specific comonent in Lazarus meant for doing that!

Sadly, Lazarus has NO help files ... so it's currently very difficult to know how the Firebird SQL data base component works or what other components you need to get it to work....
Has anyone done this successfully?
What did you use as reference material for Lazarus ?

---

