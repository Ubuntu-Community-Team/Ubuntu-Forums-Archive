---
title: "Remote desktop in desktop 2 while playing movie in desktop 1"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by sokam on 2010-03-03
I want to know if this is a functionality that can be achieve in Ubuntu.

I have two computers, a desktop (let's call it COMP#1 b/c it will get confusing) and a laptop both running 9.10.  I am able to "remote desktop" from my laptop into COMP#1 without problem (full control).  Currently, COMP#1 is connected to the TV.  If I am using COMP#1 to play video file in its workspace#1 on TV, can I remote desktop into COMP#1 workspace#2 without interference with my video which is playing on COMP#1 workspace#1?  

In another word, I want to be watching the video file on COMP#1 workspace#1 while on my laptop using "remote desktop" into COMP#1 workspace#2.

Is it possible?

---

### Post by zeroseven0183 on 2010-03-03
If this is the [Ban The User Above You]("http://ubuntuforums.org/showthread.php?t=1262941") thread, I'm going to ban you for dreaming of multitasking. ;)

Anyway, I think it's possible. All you have to see is the Workspace Switcher on the host computer.

---

### Post by cybergalvez on 2010-03-03
I'm not so sure, it possible with what comes out of the box. If you are using the standard vnc basded remote desktop that comes with ubuntu then you can't do what you want.  If however you install something like NX ([http://www.nomachine.com/](http://www.nomachine.com/)) then you log into a new session and you can do exacly what you want

---

### Post by sokam on 2010-03-04
Thanks for the link, cybergalvez.  I am looking into it.  One quick question about nx packages in the download.  Do I install the client/node/server packages on all machines involve?  or do I install client for my laptop and server package for my desktop and node on both.  I took a quick look and didn't mention anything.  Just a quick tutorial would help me get started.

---

### Post by Peter09 on 2010-03-04
Hi - you need all the packages on the server.
 
Just the client and node on the client. 
 
Also there is an app called QTNX which is the repositories which will act as an NX client. It can be installed with an apt-get or through synaptic.
 
EDIT:
I don't think QTNX supports multiple connections, but I'm not sure - so you  may need to go with the full NX client which includes a session manager.

---

### Post by sokam on 2010-03-24
NX work great as a new client session in the server.  And VNC work great as the same client session in the server (same workspace too... etc.)  However, is there any software that will let me login as the same client session in the server but I can control the session in the other available workspace to control background program which are already running.

Example, let say I am watching media file on the TV thru my computer on workspace #1 but I am also downloading files in the background using vuze.  Can I login to the same session and manage vuze (which is already running) without stopping the movie.    

This is not able to do with NX b/c whatever program already running in the first session will not show up in the new session (or is there a way to create a new session in the background and preserve it for a new user to login and out of without terminating it) and VNC will not help b/c I have to stop the media file to look at anything else in that same session.

Any magic appz out there that can do what I am thinking? Or any work around all you linux expert out there thought of?  

One solution which I have not try is to put a VM on the background and run vuze in it, then I can use VNC into the VM itself to control vuze or other background program.  However, I prefer not to b/c the thought of installing ubuntu inside ubuntu itself seem redundant if other solution is out there.

---

### Post by Peter09 on 2010-03-24
I belive in the NX configuration file of your Server (the one you are remotely attaching to) there is an option to have a new session strat up on each connection or have a shared connection. However I have never used this so I do not know if it will work.

---

