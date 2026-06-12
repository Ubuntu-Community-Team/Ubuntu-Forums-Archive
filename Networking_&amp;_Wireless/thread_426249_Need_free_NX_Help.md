---
title: "Need free NX Help"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by dyerucf on 2007-04-28
I am trying to connect to my ubuntu server but I am having issues with FreeNX


Here is what the details say on NXClient on OSX


It says it authenticated and then says Connection Timeout

______________

NX> 203 NXSSH running with pid: 9992
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.103 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: dyer
NX> 102 Password:
NX> 103 Welcome to: krumpt user: dyer
NX> 105 listsession --user="dyer" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'dyer' for reconnect:

Display Type Session ID Options Depth Screen Status Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: dyer
NX> 105 startsession --link="lan" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="0" --session="Krumpt" --type="unix-gnome" --cookie="******" --geometry="640x480+320+147" --kbtype="query" --screeninfo="640x480x32+render"

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: krumpt-1004-5B50E86261D9768CCC5AFCAFEC94B7C4
NX> 705 Session display: 1004
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: c9a2eb9aff8fea6526f152a17ef0e88d
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 1635a60f18a8d754819866974f32ca6d
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
/usr/lib/nx/nxserver: line 891: 8097 Terminated ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 105 NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.



Any Help would be great, Its my first week with ubuntu and its pretty fun so far. I am just never at home and would love to be able to admin while at the office.

Thanx
Reply With Quote

---

### Post by crmanski on 2007-04-28
> **dyerucf said:**
> I am trying to connect to my ubuntu server but I am having issues with FreeNX


Here is what the details say on NXClient on OSX


It says it authenticated and then says Connection Timeout

______________

NX> 203 NXSSH running with pid: 9992
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.103 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: dyer
NX> 102 Password:
NX> 103 Welcome to: krumpt user: dyer
NX> 105 listsession --user="dyer" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'dyer' for reconnect:

Display Type Session ID Options Depth Screen Status Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: dyer
NX> 105 startsession --link="lan" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="0" --session="Krumpt" --type="unix-gnome" --cookie="******" --geometry="640x480+320+147" --kbtype="query" --screeninfo="640x480x32+render"

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: krumpt-1004-5B50E86261D9768CCC5AFCAFEC94B7C4
NX> 705 Session display: 1004
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: c9a2eb9aff8fea6526f152a17ef0e88d
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 1635a60f18a8d754819866974f32ca6d
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
/usr/lib/nx/nxserver: line 891: 8097 Terminated ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 105 NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.



Any Help would be great, Its my first week with ubuntu and its pretty fun so far. I am just never at home and would love to be able to admin while at the office.

Thanx
Reply With Quote
It look like you are running nxclient 2.X? I have never been able to use the newer clients with freenx. You should try to find a 1.5 version client somewhere. I do not have a macosx one handy, but I'm sure you can find one.

---

### Post by dyerucf on 2007-04-28
Are you talking about the nx client for the mac or the freenx server for the the ubuntu box?

---

### Post by crmanski on 2007-04-28
I am just talking about the client.

---

### Post by icrusoe on 2007-04-30
Yes, I'm having the EXACT same problems as original poster.  Any fixes found yet?

---

### Post by dyerucf on 2007-04-30
I am still waiting for some help, let me know if you figure out anything please

---

### Post by crmanski on 2007-04-30
The freenx faq talks about a workaround. I never had sucess with it on the few machines I have used freenx.
[http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving](http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving)
As I mentioned only using an older client did the trick. A little googling found this page...
[http://www.industrial-statistics.com/info/nxclients](http://www.industrial-statistics.com/info/nxclients)

---

### Post by dyerucf on 2007-04-30
I am confussed, I have freenx installed on my ubuntu system.  I have nomachine installed on my osx macbook.  Which one do I need to upgrade or downgrade to 1.5?  the client or the server?   


John

---

