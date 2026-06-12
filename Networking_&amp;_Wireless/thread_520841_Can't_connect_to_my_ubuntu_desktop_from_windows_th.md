---
title: "Can't connect to my ubuntu desktop from windows through FreeNX :("
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2007-08-08
For some reason I cannot connect to my ubuntu desktop from the windows FreeNX 1.5 client (i tried the newer versions to and it didn't work :()

Here are my 'details' about the connection that failed, as given to me by the windows client.

[PHP]NX> 203 NXSSH running with pid: 1908
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 10.0.1.250 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: dillon
NX> 102 Password: 
NX> 103 Welcome to: GEORGE user: dillon
NX> 105 listsession --user="dillon" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-kde"
NX> 127 Sessions list of user 'dillon' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: dillon
NX> 105 startsession --session="Test" --type="unix-kde" --cache="16M" --images="64M" --link="lan" --kbtype="pc102/en_US" --nodelay="1" --encryption="1" --backingstore="never" --geometry="1280x996" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1280x996x32+render" 

NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
NX> 700 Session id: GEORGE-1000-8E152CD9C9CDB3D454EE6FCB84D1C98C
NX> 705 Session display: 1000
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: 7f77d4b128daa93e60831d9137c2007d
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 7f77d4b128daa93e60831d9137c2007d
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
NX> 105 NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1.
NX> 1006 Session status: closed
NX> 1001 Bye.
/usr/lib/nx/nxserver: line 1190: 11218 Terminated              sleep $AGENT_STARTUP_TIMEOUT
Can't open /var/lib/nxserver/db/running/sessionId{8E152CD9C9CDB3D454EE6FCB84D1C98C}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{8E152CD9C9CDB3D454EE6FCB84D1C98C}': No such file or directory

[/PHP]

I don't know if that is php code, but w/e, it makes it easier to read :p

I think the problem has something to do with SSL on the server because it looks to me like it crashes after that starts up, causing the connection to fail.

Can any of you linux pros help me out? Thanks :p.

---

### Post by kevdog on 2007-08-08
Im not sure if this guide is going to help you out, but you can use it as a checklist against your current configuration

[http://ubuntuforums.org/showthread.php?t=467219](http://ubuntuforums.org/showthread.php?t=467219)

---

### Post by ownaginatious on 2007-08-08
Aww, screw FreeNX. It's a piece of junk. I'm really starting to get frustrated about the fact that everything I want to install is either a headache to install, or just plain doesn't work because the developer simply doesn't give a crap anymore.

---

### Post by kevdog on 2007-08-09
Ok -- but Im not exactly sure if your statements are accurate.  If you have a better alternative than FreeNx (faster alternative), Im game to try it!

---

