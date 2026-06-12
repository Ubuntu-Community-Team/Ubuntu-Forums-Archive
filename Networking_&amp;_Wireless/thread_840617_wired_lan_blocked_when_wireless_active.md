---
title: "wired lan blocked when wireless active"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by mogliii on 2008-06-25
I have a desktop and a laptop.

**Desktop: **
Ubuntu 8.04
Connected via wireless to router -> internet (192.168.2.xxx)
Connected with cross-over cable to laptop (ip 192.168.0.2)

**Laptop:**
Win XP
Connected via wireless to same router as above -> internet (192.168.2.xxx)
Connected with cross-over cable to desktop (ip 192.168.0.1)



I installed samba on the linux machine to be accessed by the windows-
machine and shared one folder.

_**[SIZE="3"]The problem is[/SIZE]**_: I can only ping the
machines and connect to the samba share, if the wireless is deactivated 
on the linux-desktop. After I activate wireless again it takes ~10 
seconds before its blocked again.

Can anyone tell me how I can tell linux **not to block the traffic**. 
I have firestarter installed, and set the according devices for "internet 
connected network device" (wlan0) and "local network connected device" 
(eth0), but have not activated internet connection sharing.

Anyone any idea?

---

