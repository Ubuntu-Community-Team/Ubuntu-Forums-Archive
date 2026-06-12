---
title: "VNC/SSH  Help Please"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by Emerzen on 2007-05-08
I'm trying to get the following to work properly and keep going round in circles:

Work PC - Windows 2000 behind corporate firewall/gateway
-------->  TightVNC server running on Display 1 (5901)
-------->  PuTTY connecting to my home/Ubuntu SSH server
--------> PuTTY is forwarding local port 5901 to my home/Ubuntu server on localhost:5901




Home PC - Ubuntu Feisty (behind gateway router/software firewall)
---------> running OpenSSH (router forwards port 22 to my server & firewall open to SSH on 22)
---------> I believe that at port 5901 I should find the VNC service from work BUT
---------> when I run the following from ssh session/client---> vncviewer localhost:5901
---------> it tells me connection refused

Any thoughts?

---

### Post by dbott67 on 2007-05-09
These are the instructions that I used to setup [VNC over SSH]("http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/").

If you're trying to provide desktop support (i.e. training/troubleshooting) and need to connect to their active desktop, VNC is a good method. However, if you just require access for maintenance & updates, etc. I have found [NoMachine]("http://www.nomachine.com/download.php") to be many times faster than VNC (it's basically a terminal server that provides you with a desktop, but you cannot connect to the active session running on the desktop as far as I know) and it's secure.  There are clients for Linux, OSX, Windows & Solaris.  See attached screenshots.

Just download the 3 Debian packages and install them in this order:

1. NX Client
2. NX Node
3. NX "Free Edition" Server

The admin manual is [here]("http://www.nomachine.com/documentation/admin-guide.php").


On the other had, if you just want to provide remote support (like I do for countless people) and encryption is not a priority, then you can always try "[Reverse VNC]("http://ubuntuforums.org/showthread.php?t=299489")". This method is firewall-friendly; no port-forwarding at the client end. Just make sure your firewall is forwarding 5500 to your desktop and you've got vncviewer running in "listen" mode.

As for your problem, we need to verify a few things:

1. Can you connect locally to your home computer via SSH & VNC?
2. Can you post the output of the following 2 commands from your home PC?  This will verify whether the ssh & VNC services are listening:
```
dbott@feisty:~$ **netstat -l | grep 590**
tcp6       0      0 *:5900                  *:*                     LISTEN

``````
dbott@feisty:~$ **netstat -l | grep ssh**
tcp6       0      0 *:ssh                   *:*                     LISTEN

```

-Dave

---

### Post by Emerzen on 2007-05-09
Hi and thanks for your wonderful post.  I did get it to work as the mistake I was making was assuming that the VNC-server was sending data over it's port but instead it's listening.  So, I had to change my PuTTY from forwarding the port to a reverse forward from home to the port.  After that I had to bind my home port dynamically to the localhost and all was well.  I work in healthcare so encryption is a must.

However, I'm going to be doing a reinstall of Feisty as I'm adding new hardware this weekend, and that will give me an opportunity to try your alternatives.  Again, thank you very much your reply was very kind and appreciated.

---

