---
title: "NXserver stopped working after enabling Compiz"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by kocela on 2007-08-25
Hi, 

I had nxserver set up and working fine. 
I then installed compiz and enabled my ati drivers which is working fine however now when i try to use nx to connect from my XP machine I am getting the following error. 
Was getting the 556 error so I changed the permissions on .Xauthority
after i did that I now see the screen start to load but as it tried to switch to the Desktop view I get kicked out. The error log reads as follows.

Aug 25 18:51:19 Ubuntu NXSERVER-3.0.0-63[21216]: User 'kocela' logged in from '192.168.1.99'. 'NXLogin::set'
Aug 25 18:51:19 Ubuntu NXSERVER-3.0.0-63[21216]: Selected node host:localhost with port:22 'main::selectNode'
Aug 25 18:51:19 Ubuntu NXSERVER-3.0.0-63[21216]: Current selected node: localhost is in status: running  'main::selectNode'
Aug 25 18:51:19 Ubuntu NXSERVER-3.0.0-63[21216]: Selected session type: unix-gnome allowed in the profile of user: kocela 'NXShell::Static'
Aug 25 18:51:21 Ubuntu NXSERVER-3.0.0-63[21216]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Aug 25 18:51:24 Ubuntu NXSERVER-3.0.0-63[21216]: Session '7E9EB12E16655B28819F1BE5A6CBBECB' started by user 'kocela'. 'NXShell::handler_session_start'
Aug 25 18:51:24 Ubuntu NXSERVER-3.0.0-63[21216]: ERROR: run command: no child process with pid 21229 Logger::log nxserver 3061
Aug 25 18:51:24 Ubuntu NXSERVER-3.0.0-63[21216]: User 'kocela' from '192.168.1.99' logged out. 'NXLogin::reset'
Aug 25 18:51:24 Ubuntu NXNODE-3.0.0-76[21236]: Using port '1008' on node 'Ubuntu' for session 'unix-gnome'. Logger::log nxnode 5733
Aug 25 18:51:24 Ubuntu NXNODE-3.0.0-76[21236]: Using host from available host list: 'localhost'. Logger::log nxnode 5734
Aug 25 18:51:30 Ubuntu gconfd (kocela-5209): Resolved address "xml:readwrite:/home/kocela/.gconf" to a writable configuration source at position 0
Aug 25 18:51:41 Ubuntu NXNODE-3.0.0-76[21236]: ERROR: Unexpected termination of nxagent because of signal: 11 Logger::log nxnode 3752
Aug 25 18:51:41 Ubuntu NXNODE-3.0.0-76[21236]: ERROR: run command: process: 21252 died because of signal: 11 Logger::log nxnode 3759
Aug 25 18:51:42 Ubuntu NXNODE-3.0.0-76[21259]: ERROR: Error when monitoring session: Unexpected termination of nxagent 'NXSessionMonitor::__setSessionStatus'
Aug 25 18:51:43 Ubuntu NXNODE-3.0.0-76[21259]: Directory '/home/kocela/.nx/C-Ubuntu-1008-7E9EB12E16655B28819F1BE5A6CBBECB' renamed into '/home/kocela/.nx/F-C-Ubuntu-1008-7E9EB12E16655B28819F1BE5A6CBBECB' for further investigation Logger::log nxnode 5911
Aug 25 18:51:43 Ubuntu NXNODE-3.0.0-76[21259]: session monitor: cleaning session files: removing '/tmp/.X11-unix/X1008' Logger::log nxnode 8449
Aug 25 18:51:43 Ubuntu NXNODE-3.0.0-76[21259]: session monitor: cleaning session files: removing '/tmp/.X1008-lock' Logger::log nxnode 8458
Aug 25 18:51:44 Ubuntu NXNODE-3.0.0-76[21236]: Session 'unix-gnome' on port '1008' failed. Logger::log nxnode 5990
Aug 25 18:51:46 Ubuntu NXSERVER-3.0.0-63[21255]: ERROR: NXNodeExec: Cannot kill nxssh process: No such process 'NXNodeExec::exec'
Aug 25 18:51:46 Ubuntu NXSERVER-3.0.0-63[21255]: User 'kocela' from '192.168.1.99' logged out. 'NXLogin::reset' 

Any Ideas???

---

### Post by kevdog on 2007-08-25
Couple things to clarify

1. Can you plain ssh into the server?

2. On the server side inside the .nx directory, have you deleted all the C-xxxx-100x-xxxxxx files.  Im not sure what you are using as the client, however have you cleared out the corresponding files client side?

---

### Post by kocela on 2007-08-26
Thanks for the relpy.

Yes i am able to ssh without issue.

I am using the windows nxclient, and I have tried to clear out all the all the C-xxxx-100x-xxxxxx files however it did not help.

---

### Post by DLGandalf on 2007-08-29
I've got the exact same symptoms

have you found a solution by now? I sure hope so

//edit
ow it's only been 3 days since you started this thread :)

---

### Post by surlyjake on 2007-10-22
me three

---

### Post by surlyjake on 2007-10-22
actually, i figured a way around my problem:

i am running kubuntu gutsy. nx was working, then i enabled compiz. after i enabled compiz, nx stopped working. it would start the connection, i saw my loading screen, and it would give me a connection error. 

What i did:

ssh to the server machine.
create a new user:
```
/sudo /usr/NX/bin/nxserver --useradd <a new username> --system
```

after that, i could log on using NX perfectly using the new user. now to figure out how to get to my NORMAL desktop...

---

### Post by DeFrancoj on 2007-12-02
yeah i think that's simply because the new user by default does not have compiz enabled. The same thing happened to me. If you disable compiz I bet you'd be able to run an NX session with your own username.  The question is, how can we make an NX session know to turn off compiz instead of just failing.

---

### Post by daflame on 2007-12-10
> **DeFrancoj said:**
> yeah i think that's simply because the new user by default does not have compiz enabled. The same thing happened to me. If you disable compiz I bet you'd be able to run an NX session with your own username.  The question is, how can we make an NX session know to turn off compiz instead of just failing.

It all depends on the way that you run Compiz, either AIGLX, NVIDIA, or XGL.  With Xgl you can look for a process of Xgl matching the current display.  if you could intercept the script to check the X server version before loading Compiz that might help.  The other way is to create a separate Xorg configuration file and use it exclusively for NX.  That could solve many problems that people commonly suffer from in NX.

---

### Post by partriv on 2007-12-28
I am getting this same error:
ERROR: Unexpected termination of nxagent because of signal: 11

while using eclipse.  Does anyone know how I can fix this?  I am using the vesa drivers, can compiz run under the vesa drivers?  Is this  confirmed compiz problem?

I can be logged into my nomachine session working, and randomly, while using eclipse, the session just dies.  This appears in /var/logs/messages
Dec 28 18:44:19 picdev1 NXNODE-3.1.0-3[5427]: ERROR: Unexpected termination of nxagent because of signal: 11 Logger::log nxnode 3775
Dec 28 18:44:19 picdev1 NXNODE-3.1.0-3[5427]: ERROR: run command: process: 5452 died because of signal: 11 Logger::log nxnode 3782
Dec 28 18:44:20 picdev1 NXNODE-3.1.0-3[5458]: ERROR: Error when monitoring session: Unexpected termination of nxagent 'NXSessionMonitor::__setSessionStatus'


Any ideas?  It is very frustrating :(

---

