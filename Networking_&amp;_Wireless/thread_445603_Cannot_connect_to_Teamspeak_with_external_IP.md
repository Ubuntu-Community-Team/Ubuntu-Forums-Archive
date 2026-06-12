---
title: "Cannot connect to Teamspeak with external IP"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by Flibbertygibbit on 2007-05-16
First of all, I am very new to Linux and also to this forum, so please bear with me.

I have recently used [this guide]("http://ubuntuforums.org/showthread.php?t=236834") to install a Teamspeak server on my Ubuntu machine. I am able to connect the client by inputting the local IP address (192.168.1.100) but not with the external address. I can also connect in the same way with other computers on my network. I haven't been able to try it from outside my network, but I assume it won't work.

I do have a router and initially I thought my router wasn't forwarding the port, but it's set up correctly. I installed Firestarter and created inbound policies to open the ports for Teamspeak (8767 and 14534) but it didn't seem to help. I'm not sure if it has anything to do with the problem or not, but I noticed that in the active connections in Firestarter, the Teamspeak server has a source IP of 127.0.1.1 while everything else is 192.168.1.100.

I would appreciate any help and hopefully I can learn something in the process. If any more information is needed to troubleshoot the problem, just ask and I'll provide it.

---

### Post by Flibbertygibbit on 2007-05-19
I am still having problems with this issue. If anybody can help or has ideas on where I can look for a solution, I would greatly appreciate it.

---

### Post by Flibbertygibbit on 2007-05-22
This issue was resolved.

---

### Post by vange on 2007-11-06
> **Flibbertygibbit said:**
> This issue was resolved.

How did you resolve the issue - I am trying to help a guy on Ubuntu. I am running Kubuntu myself.

---

