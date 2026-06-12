---
title: "[SOLVED] Can't see Windows network"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by chiuczek on 2008-09-05
I am a complete Linux novice, dual-booting on a laptop and I am trying to configure Ubuntu to see my Windows network. I have one XP machine configured to share a printer and some folders, and it works fine accessing it under Windows on the same machine. In Ubuntu, however, I can't even see the workgroup that the machine is under. I have followed lots of guides for networking Linux to Windows, but nothing seems to deal with my problem. The XP machine won't return pings or anything. I have a feeling it may be something to do with the router, but it does work without trouble under XP.
Any help would be appreciated.

---

### Post by Iowan on 2008-09-05
Problems seeing Windows networks seems to be a recurring theme... however, **ping** problems are slightly different.  
Will the router return pings?  (**ping** router IP address).
Does Ubuntu box get an address in same subnet as XP box? (**ifconfig**)
Does the XP box have firewall active? 
Does router have problems with IPv6?

---

### Post by chiuczek on 2008-09-10
Turned out to be the firewall on the XP box, thanks for your help.

---

