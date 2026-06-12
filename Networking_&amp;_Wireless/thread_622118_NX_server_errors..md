---
title: "NX server errors."
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by psychrometric on 2007-11-24
Sorry for being a noob to ubuntu &#8230; I installed the client, node, server, as well as ssh on my ubuntu desktop. I then try to connect to it from my vista laptop, but I am getting the following error every time I try to connect to. 
I hope someone can help me.
> 
NX> 203 NXSSH running with pid: 5840
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.65 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.0.0-79 - LFE
NX> 105 Hello NXCLIENT - Version 3.0.0
NX> 134 Accepted protocol: 3.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: giorgos
NX> 102 Password: ***
NX> 103 Welcome to: servbot user: giorgos
NX> 105 Listsession --user="giorgos" --status="suspended\054running" --geometry="1280x800x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
1001    unix-kde         C7F9308804762EB690DEFFAE97932411 -RD--PSA    32 1280x772       Suspended   serv                          

NX> 148 Server capacity: not reached for user: giorgos
NX> 105 Restoresession --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="serv" --type="unix-gnome" --geometry="800x600" --client="winnt" --keyboard="pc102\057gb" --id="C7F9308804762EB690DEFFAE97932411" --resize="1" 
NX> 596 NX> 596 ERROR: NXNODE Ver. 3.0.0-93  (Error id e043DB8)
NX> 596 NX> 596 ERROR: resume session: run commands
NX> 596 NX> 596 ERROR: execution of last command failed
NX> 596 NX> 596 last command: /bin/bash --login -c 'kill -USR2 6760'
NX> 596 NX> 596 exit value: 1
NX> 596 NX> 596 stdout: 
NX> 596 NX> 596 stderr: /bin/bash: line 0: kill: (6760) - No such process
NX> 596 NX> 596 init: stdin arguments: user=giorgos,userip=192%2e168%2e1%2e69,uniqueid=C7F9308804762EB690DEFFAE97932411,display=1001,images=64M,cache=16M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=serv,shmem=1,type=unix-kde,virtualdesktop=1,resize=1,id=C7F9308804762EB690DEFFAE97932411,keyboard=pc102%2fgb,geometry=800x600,link=adsl,render=1,subscriptionid=None,productid=LFE,balance_host=192%2e168%2e1%2e65,encryption_mode=3,connection=local
NX> 280 Exiting on signal: 15

---

### Post by kevdog on 2007-11-24
Try to clear all the old sessions -- Nx server is good, but sometimes chokes on trying to restore old sessions - hence you need to clean out old nx sessions in windows and on the server.

---

### Post by psychrometric on 2007-11-25
Thanks for your reply. I uninstalled and reinstalled everything. Now I seem to get closer to connecting, but not there yet&#8230; In the &#8216;Available Sessions&#8217; list I get a &#8216;Running&#8217; status, I then double click on the session, and I get the following error.

> 
&#8230;&#8230;.
cat: /var/lib/nxserver/db/running/sessionId{9645C9E5EE650EED0C59330FAD4F8FD0}: No such file or directory
NX> 280 Exiting on signal: 15

Any help would be greatly appreciated. I really need this.

---

### Post by kevdog on 2007-11-25
It sounds like something is wrong with the client -- meaning the client stored the variable sessionId{9645C9E5EE6 50EED0C59330FAD4F8FD0}, and it trying to access it.  Also I cant remember but on the server side, there are also directories in your home directory.  Something like .nxserver or .nxconfig.  If you do a ls -la and look for the directories starting with . you should find it.  Reinstallation does not clean up these directories to the best of my knowledge.

---

