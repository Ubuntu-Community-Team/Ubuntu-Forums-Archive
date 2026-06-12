---
title: "VNC tunneling through SSH problem"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by Skerit on 2007-04-28
I'm trying to access my parent's computer back home, 40 km away. They're both Ubuntu machines. 

The other PC is running the openssh server, which is working great, I can connect to it without any problem...

So, because we're both using routers and stuff, and port forwarding crap and all, I using the following command:

**[CENTER]ssh -L 5800:bla.dnsalias.com:5900 [email]user@bla.dnsalias.com[/email][/CENTER]**

That SHOULD forward my local port (5800) to the remote port 5900, but jvncviewer won't do anything:

**[CENTER] jvncviewer localhost::5800[/CENTER]**

It asks for my password, which I enter correctly, and then it stops. Connection refused. And then the remote box gives the following error:

**[CENTER]channel 3: open failed: connect failed: Connection refused[/CENTER]**

So I must have forgotten something, I just have no idea what it is ...

---

### Post by dbott67 on 2007-04-28
These are the instructions that I used to setup [VNC over SSH]("http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/").

If you're trying to provide desktop support (i.e. training/troubleshooting) and need to connect to their active desktop, VNC is a good method.  However, if you just require access for maintenance & updates, etc. I have found NoMachine to be many times faster than VNC (it's basically a terminal server that provides you with a desktop, but you cannot connect to the active session running on the desktop as far as I know) and it's secure.

On the other had, if you just want to provide remote support (like I do for countless people) and encryption is not a priority, then you can always try "[Reverse VNC]("http://ubuntuforums.org/showthread.php?t=299489")".  This method is firewall-friendly; no port-forwarding at the client end.  Just make sure your firewall is forwarding 5500 to your desktop and you've got vncviewer running in "listen" mode.

-Dave

---

### Post by Skerit on 2007-04-28
Ah, thanks, gonna try them all out, however I do need to be able to get access to an existing session, there are 2 computers, one with all the music on it, and also for their personal use, and there's another one they use to play music in the restaurant, so when they mess up I should be able to help out, anyway, thanks so far! :)

---

