---
title: "Telnet to XP Home"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Eviltechie on 2008-09-07
I am running Ubuntu 8.04, and was wondering how I could telnet to a computer running XP Home Edition. I tried telnet 192.168.2.32 (its IP), but nothing happened. Will I need to install something on the XP computer?

---

### Post by lswb on 2008-09-07
A telnet server program would have to installed and configured to run on the XP system. If you can find an SSH server instead it would provide much better security. The 192.168.x.x address range can only be accessed on your local network, so maybe security is less of a concern.

A google search for "telnet server for windows XP" or "ssh server for windows XP" gives plenty of hits, try some of those.

---

### Post by forger on 2008-09-07
That's an internal IP, the computer with XP is connected through a router/hub with the other computer?

Why not just use the Applications > Internet > Remote Desktop Viewer ?
I think that you can use the Remote assistance: [http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx](http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx)
Otherwise, you need to setup a vnc server on XP such as [http://www.tightvnc.com/](http://www.tightvnc.com/)

---

### Post by lswb on 2008-09-07
A telnet server program would have to installed and configured to run on the XP system. If you can find an SSH server instead it would provide much better security. The 192.168.x.x address range can only be accessed on your local network, so maybe security is less of a concern.

A google search for "telnet server for windows XP" or "ssh server for windows XP" gives plenty of hits, try some of those.

---

