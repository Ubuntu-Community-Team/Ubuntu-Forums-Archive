---
title: "Remote Access ?"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by jboywer on 2010-08-06
Please!! could someone show a step by step instructions showing how to setup remote access.

---

### Post by MattBD on 2010-08-06
What sort of remote access do you mean? It may be possible to do what you want remotely from the command line via SSH, or do you need to use a GUI?

---

### Post by Elmer Fudd on 2010-08-06
As requested by MattBD- More detail please.
Something like ...  I have a computer running 10.04 at home on a router running NAT. I want to log into it for data? support?  I want to be able to log into it from a Win7 or Linux machine. I want to be able to do it with no one there or only with someone there to accept the remote connection.

The more detail, the better answer you will get.

---

### Post by jboywer on 2010-08-20
okay i am using the gui, I know there are 3rd party remote access software like logmein.com for instance, but i wanted to set up remote access similar to that of windows xp. I am using ubuntu 10.4

---

### Post by cybergalvez on 2010-08-20
> **jboywer said:**
> okay i am using the gui, I know there are 3rd party remote access software like logmein.com for instance, but i wanted to set up remote access similar to that of windows xp. I am using ubuntu 10.4

if you are looking for "rdp" like access then either 
[freenx]("https://help.ubuntu.com/community/FreeNX")
[nomachine]("http://www.nomachine.com/")
[x2go]("http://www.x2go.org/index.php?id=1&L=5")
will give you exactly what you want. 
If however, you want something more like logmein which will allow you to login to a running session then ssh tunneling with the built in vnc is the way to go (I do this with my Mother so I can see what she is talking about when she has a problem) and there are plenty of tutorials on how to do that.

---

### Post by Thomas Garman on 2010-08-20
In System > Preferences you will see "Remote Desktop"
 
turn it on and check the appropriate boxes.  Then go to Applications > Internet > Remote Desktop Viewer
 
You will need to put the isp of the computer your a remotely controlling in and select VNC.  It's screen will appear and you can control it remotely (if remote desktop is turn on for the computer you want to control).

---

### Post by Grenage on 2010-08-20
If you enable **any** remote desktop software, use a damn good password (or key)!

---

### Post by bodhi.zazen on 2010-08-20
If you are connecting over the internet use FreeNX or ssh.

You can forward X applications over ssh, Xming runs on Windows (and is portable on a flash drive). putty and winscp are windows ssh clients.

---

