---
title: "Help Needed with VNC between K and X Ubuntu"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by eagle416 on 2008-12-31
I really have no idea how to go about this. My Grandma's PC has Xubuntu Intrepid. When she has problems I want to be able to login from my Kubuntu Hardy Laptop to drive her computer. I installed vncserver, and tried to start it (this is my fourth attempt).

```
epeach@PEACH3:~$ sudo vncserver

New 'PEACH3:4 (root)' desktop is PEACH3:4

Starting applications specified in /home/epeach/.vnc/xstartup
Log file is /home/epeach/.vnc/PEACH3:4.log
```

From Kubuntu then, I start Krdc and type in the Remote Desktop box: "PEACH3:4" and hit connect, and it says "Connection Failed. A server with the given name cannot be found." Well there is one, it's sitting with its Ethernet cable right there in the router next to mine.

Can anybody please help me out?

---

### Post by blueridgedog on 2009-01-01
A few suggestions.  Try the IP of the computer and the :4 (for fourth display I assume), such as:

192.168.1.102:4

As a connection string for VNC.  I can't see how a given machine on the network can resolve the name "PEACH" into an IP unless you have a more complex network than I imagine.

Also, if you have tried several times to do this, ie you are up to the 4th attempt, you probably have four or more VNC servers running.  You can check this by bringing up a terminal and typing in:

ps ax | grep vnc

A reboot should clear them up and you can try it from the start using IP addresses.

---

### Post by eagle416 on 2009-01-01
All right, the IP address worked. It logged me into a bash terminal as root, and I successfully created a text file to prove i was there. Now for a few more questions.

I wanted to set up a system where the person at the Xubuntu computer could see the mouse moving around the screen (for the purposes of tech support), observing the changes I make as I do them. I also want to login with the running applications appearing as windows on my screen so I can see exactly what is happening at the time. how can I make this happen?

Secondly, after I leave by closing my window on Kubuntu, I run the "ps ax | grep vnc" on Xubuntu, but not only can I not restart vncserver, I cannot start any other applications. If I close the terminal, I cannot reopen it until I reboot.

What's going on with that?

---

### Post by blueridgedog on 2009-01-01
try connecting to session :0 or session :1 to see if you the session your Grandmother is looking at.

---

