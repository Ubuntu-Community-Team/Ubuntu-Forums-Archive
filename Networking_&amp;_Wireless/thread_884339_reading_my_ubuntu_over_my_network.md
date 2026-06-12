---
title: "reading my ubuntu over my network"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by mastermarko on 2008-08-08
how do i get windows xp to find my ubuntu on the network  i am only new to linux and any help would be great and as far as it goes i dont no much more about windows lol

---

### Post by Iowan on 2008-08-09
Start by verifying that windows can **ping** Ubuntu.

Learn Ubuntu's IP address by running **ifconfig** from a terminal.  Same information is available (on my 7.10 machine) under System>Administration>Network Tools. Under Network Device, choose  Ethernet Interface. The IPv4 address is probably the one you want.  May be different on Gutsy (8.04).

I ordinarily use Windows (XP) START>Run "CMD" to get a command prompt (Ahhh, the good ol' days...) **ping 192.168.1.2** (substitute the Ubuntu address).  

This is only the first step.  I suspect what you *really* want is to share files - which will require [Samba.]("https://help.ubuntu.com/community/SettingUpSamba")

---

