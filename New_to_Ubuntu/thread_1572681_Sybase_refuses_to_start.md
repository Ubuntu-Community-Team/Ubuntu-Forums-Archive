---
title: "Sybase refuses to start"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-09-11
Question: I've installed the developer edition from
[http://www.sybase.com/linux](http://www.sybase.com/linux)

First it complained about
libaio.so.1 not found

So I installed libaio1
apt-get install libaio1

Then, the installation worked, but the server didn't start and below is the log of why. 
I restarted and tried again (since it might not have loaded a kernel module), but I got the same message...

> 
Kernel  Warning: Using default file '/opt/sybase/Sybase155.cfg' since a configuration file was not specified. Specify a configuration file name in the RUNSERVER file to avoid this message.
00:00:00000:00000:2010/09/11 20:17:47.23 kernel  os_create_region: can't allocate 71708672 bytes
00:00:00000:00000:2010/09/11 20:17:47.23 kernel  kbcreate: couldn't create kernel region.
00:00:00000:00000:2010/09/11 20:17:47.23 kernel  kistartup: could not create shared memory
00:00:00000:00000:2010/09/11 20:17:48.01 kernel  The configuration area in device '/opt/sybase/data/master.dat' appears to be corrupt. The server cannot continue and will shut down.


From what I interprete it, there is not enough shared memory available.
How do I make more shared memory available ?
I still have some 800 MB of RAM left...

---

### Post by WitchCraft on 2010-09-11
Problem solved.
In case anybody else has the problem:

Edit your /etc/sysctl.conf and add the following line:
```

kernel.shmmax = 200000000

```

this reserves appx. 200 MB shared memory.

Then one still needs to change the current configuration:
```

echo "200000000" > /proc/sys/kernel/shmmax

```
or just restart.

Run
```

sysctl -a | grep shmma

```

to verify whether the settings are actually in effect.

---

### Post by WitchCraft on 2010-09-11
Oops, that was premature. I now get a


```


Sep 11 22:09:20 2010: msgid:20071 -- os_create_region: shmat(5242896): Invalid argument
Sep 11 22:09:20 2010: Warning: Attempt to create shared memory at addr=0xb8000000 failed
Sep 11 22:09:20 2010: Now trying at addr=0xb9000000
Sep 11 22:09:20 2010: msgid:20071 -- os_create_region: shmat(5275664): Invalid argument
Sep 11 22:09:20 2010: Warning: Attempt to create shared memory at addr=0xb9000000 failed
Sep 11 22:09:20 2010: Now trying at addr=0xba000000
Sep 11 22:09:20 2010: msgid:20071 -- os_create_region: shmat(5308432): Invalid argument
Sep 11 22:09:20 2010: Warning: Attempt to create shared memory at addr=0xba000000 failed
Sep 11 22:09:20 2010: Now trying at addr=0xbb000000
Sep 11 22:09:20 2010: msgid:20071 -- os_create_region: shmat(5341200): Invalid argument
Sep 11 22:09:20 2010: Warning: Attempt to create shared memory at addr=0xbb000000 failed
Sep 11 22:09:20 2010: Now trying at addr=0xbc000000
Sep 11 22:09:20 2010: msgid:20071 -- os_create_region: shmat(5373968): Invalid argument
Sep 11 22:09:20 2010: Warning: Attempt to create shared memory at addr=0xbc000000 failed
Sep 11 22:09:20 2010: Now trying at addr=0xbd000000
Sep 11 22:09:20 2010: msgid:20071 -- os_create_region: shmat(5406736): Invalid argument
Sep 11 22:09:20 2010: Warning: Attempt to create shared memory at addr=0xbd000000 failed
Sep 11 22:09:20 2010: Now trying at addr=0xbe000000
Sep 11 22:09:20 2010: msgid:20071 -- os_create_region: shmat(5439504): Invalid argument

```

Error when installing monitoring server...
Anybody knows what that means?
Kernel interface changed ?

---

### Post by WitchCraft on 2010-09-12
Bump.

---

### Post by WitchCraft on 2010-09-12
This is utter ********.

First, you have to install a dependency with no prior info, then you need to increase a kernel setting, with no prior info, and no official documentation or mentioning it in the readme.

The closest thing one can find is this:
[http://www.happy-hacking.com/index.php/Sybase_ASE_15.0.2_on_Ubuntu](http://www.happy-hacking.com/index.php/Sybase_ASE_15.0.2_on_Ubuntu)

Then, monitor server won't install for whatever reason.

Then, when your computer restarts, you find out sybase doesn't start automatically.
Not because the database is not set to start automatically, which would be proper, but because there is no start/stop script at all. First you have to google for such a script...

When you finally find one that works, such as here
[http://blog.cachemiss.com/articles/Sybase%20Init%20Script.pod](http://blog.cachemiss.com/articles/Sybase%20Init%20Script.pod)

You realize there is no graphical tool.
So downloading razorsql visual sql tool, but connection refused everytime. No additinal info.

Worse, you cannot connect with isql, the command line tool, for whatever reason.

For a commercial product, I must say...
They want several thousand bucks a year, but they aren't even capable of writing an installer that works, nor document it properly, nor deliver a working administration tool...

With PostGre or FireBird, I get an installer that works out of the box, and GUI tools are available,too (although somewhat old and inadequate). 
But they are completely free.

This is soooo frustrating.
I wonder if they ever tested their product at all.

---

### Post by WitchCraft on 2010-09-17
bump.

---

### Post by WitchCraft on 2010-09-22
bump.

---

### Post by WitchCraft on 2010-09-24
bump.

---

### Post by WitchCraft on 2010-09-25
Wow, finally solved, f*ing unbelievable.

The GUI is located in:
/opt/sybase/shared/sybcentral600/

Which wouldn't be a problem if they had documented it, so you hadn't to search and also try every script in every directory (many directories, and every time you need to set the environment variables), only to find that the GUI is in the shared directory. 
It must be sooo difficult to add a menu entry to gnome.

To start it, you need to do this:
export SYBROOT="/opt/sybase/"
export SYBASE_JRE6="/usr/lib/jvm/jdk1.6.0_20_-sun/jre/"

Also, you need to run:
/opt/sybase/ASE-15_0/install/showserver

in order to verify whether the server actually runs.
In my case, the problem was that in the mean-time, it crashed from all the trying...

Then you can start the GUI with:
/opt/sybase/shared/sybcentral600/scjview.sh

And by the way, the servername is not the servername you enter at installation, it's actually the hostname, but without \servername...

The command line tool seems not to work, whatever.
(
> 
Using locale name "en_US.utf8" defined in environment variable LANG
Locale name "en_US.utf8" doesn't exist in your /opt/sybase/locales/locales.dat file
An error occurred when attempting to allocate localization-related structures.
)


F*ing unbelievable. The amount of time wasted.

And now that it doesn't matter anymore, I found this one:
[http://blog.fpmurphy.com/2010/07/installing-sybase-ase-15-5-on-fedora-13.html](http://blog.fpmurphy.com/2010/07/installing-sybase-ase-15-5-on-fedora-13.html)

for Fedora...


By the way, this is how to connect via mono/.NET:
```

ODBC :
Standard Sybase System 12 (or 12.5) Enterprise Open Client:
"Driver={SYBASE ASE ODBC Driver};Srvr=Server1;Uid=username;Pwd=password"

Standard Sybase System 11:
"Driver={SYBASE SYSTEM 11};Srvr=Server1;Uid=username;Pwd=password;"

Intersolv 3.10:
"Driver={INTERSOLV 3.10 32-BIT Sybase};Srvr=Server1;Uid=username;Pwd=password;"

Sybase SQL Anywhere (former Watcom SQL ODBC driver):
"ODBC; Driver=Sybase SQL Anywhere 5.0;
DefaultDir=c:\dbfolder\;Dbf=c:\mydatabase.db;Uid=u sername;Pwd=password;Dsn="""""

Note! The two double quota following the DSN parameter at the end are escaped quotas (VB
syntax), you may have to change this to your language specific escape syntax. The empty
DSN parameter is indeed critical as not including it will result in error 7778.

AseConnection (.NET)

Standard:
"Data Source='myASEserver';Port=5000;Database='myDBname' ;UID='username';PWD='password';"

Declare the AseConnection:
C#:
using Sybase.Data.AseClient;
AseConnection oCon = new AseConnection();
oCon.ConnectionString="my connection string";
oCon.Open();

VB.NET:
Imports System.Data.AseClient
Dim oCon As AseConnection = New AseConnection()
oCon.ConnectionString="my connection string"
oCon.Open()

```

F*ing unbelievable. I have Sybase working.

---

### Post by Logisch on 2011-02-24
I experienced the same frustration and waste of time when installing Sybase 15.5 on Ubuntu 9.0 32 bit.

> The command line tool seems not to workSame problem here.

In:
/opt/sybase/locales/locales.dat

Find the section:
[linux]

I had to add the line:
    locale = en_NZ.UTF-8, us_english, iso_1


Other useful stuff I used was...
The log file: /opt/sybase/ASE-15_0/install/HOSTNAME.log
Uninstall: /opt/sybase/sybuninstall/ASESuite/uninstall
Connect: ./opt/sybase/OCS-15_0/bin/isql -Usa -P -SHOSTNAME


And I still can't run stuff like the /opt/sybase/ASEP/aseplugin

First I got:
Error: $SYBROOT variable not set
Which I solved by:
export SYBROOT=/opt/sybase/

Then I got:
Error: You need to set $SYBASE_JRE6 to the directory where your Java JRE is installed.
Tried:
export SYBASE_JRE6=/var/java/jdk1.6.0_16/jre

But the result just becomes:
-e
exec: 319: /bin/java: not found

(and same thing for the /opt/sybase/shared/sybcentral600/scjview.sh)

---

