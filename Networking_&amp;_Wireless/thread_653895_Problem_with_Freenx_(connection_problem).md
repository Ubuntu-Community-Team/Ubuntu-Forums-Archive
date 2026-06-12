---
title: "Problem with Freenx (connection problem)"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by DaDisbe on 2007-12-30
Hello,

First, sorry about my english ...

I tried to install freenx on Ubuntu server 7.10 and i have some problems...
I think the installation is fine, but I have a problem when I connect from 
a windows client with NoMachine. Nxserver : 2.1.0 Client : 1.5

When I click "Login" I have : 	-Connecting 192.168.1.67 (server adress)
				-Connected to 192.168.1.67
				-Waiting Authentification
				-Authentification complete
				-I have this : 
[[img]http://www.hostingpics.net/thumbs/638114image0.jpg[/img]]('http://www.hostingpics.net/pics/638114image0.jpg')
				-I click "New"
				-Creating the new sessions
				-And then I get this message : 
[[img]http://www.hostingpics.net/thumbs/191784image1.jpg[/img]]('http://www.hostingpics.net/pics/191784image1.jpg')


So this is sshlog :
```

NX> 203 NXSSH running with pid: 3084
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.1.67 on port: 555
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-71 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: dad
NX> 102 Password: 
NX> 103 Welcome to: Serveur user: dad
NX> 105 listsession --user="dad" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'dad' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        371D832E14AE80C2FADAF3B55D6CE195 --------       1280x1024      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: dad
NX> 105 listsession --user="dad" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'dad' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       vnc-local        6582E360310C80997E3E871344214DA5 --------       1280x1024      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: dad
NX> 105 startsession --session="Serveur" --type="unix-gnome" --cache="16M" --images="64M" --link="lan" --kbtype="pc102/us" --nodelay="1" --encryption="1" --backingstore="never" --geometry="1280x996" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1280x996x32+render" 

NX> 1000 NXNODE - Version 2.1.0-71 OS (GPL)
NX> 700 Session id: Serveur-1001-7EFBBCFFE429CF4F1A4A9D37B4C578EB
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: ae579faced6ee43f55f26c7803aae2d9
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: ae579faced6ee43f55f26c7803aae2d9
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
/usr/lib/nx/nxserver: line 1283: 17353 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 105 NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/dad/.nx/F-C-Serveur-1001-7EFBBCFFE429CF4F1A4A9D37B4C578EB/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
Can't open /var/lib/nxserver/db/running/sessionId{7EFBBCFFE429CF4F1A4A9D37B4C578EB}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{7EFBBCFFE429CF4F1A4A9D37B4C578EB}': No such file or directory
NX> 1006 Session status: closed
Killed by signal 15.

```


And here : /home/dad/.nx/F-C-Serveur-1001-xxxxxxxxxxxxxxxxxxxx/session
```

Error: Aborting session with 'Unrecognized option: -fp/usr/share/fonts/X11/misc$
Session: Aborting session at 'Sun Dec 30 18:31:24 2007'.
Session: Session aborted at 'Sun Dec 30 18:31:24 2007'.
xrdb: Connection refused
xrdb: Can't open display ':1001'
/usr/lib/nx/nxnode: line 317: /usr/bin/dbus-launch: No such file or directory

```

Do u have ideas ?

Thank You !

---

### Post by DaDisbe on 2008-01-01
up ! (and happy new year :) )

---

### Post by DaDisbe on 2008-01-02
Hey all !

That works, I found my problem , This is a solution :KS:

In node.conf , I set this line -> 
```
AGENT_EXTRA_OPTIONS_X="-fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
```
Thanks to *GSBoomer* !

I installed XFCE4 (+/- 100Mo) on the server and i choose these options on the client (Windows)

-> In **General Settings**, **Desktop** I choose **Unix** and **Custom** , then I clicked **Settings** Choose **Run the following command** and this command: ```
startxfce4
```
Then choose **New Virtual Desktop**

Restart nxserver 
```
nxserver --restart
```

And it Works Perfectly ! :guitar:

---

