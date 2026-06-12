---
title: "[SOLVED] Moved PC lost network connection"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by Merovius on 2008-10-20
I set up a dual boot XP / Ubuntu 8.04 system for my son in law. All worked well here at my place. He took it home and set it up. XP has a good wired Internet connection. Ubuntu has none. Its like Ubuntu thinks it has no connection at all.

Network tools shows Loopback Interface (lo) and Ethernet Interface (eth0)

Seems like it sees the card. Could it be the change of routers from my place to his? He didn't really want to reboot the router because of the other wired and wireless PC's in the house. 

Ideas welcome..:confused:

TIA

---

### Post by Iowan on 2008-10-20
Ubuntu set up for DHCP or roaming?  It's probably a bit difficult to check things like **ifconfig** and contents of */etc/network/interfaces* file.

---

### Post by Merovius on 2008-10-20
It should be set to whatever a default clean install would be set to. He did mysteriously get a connection then it disappeared on rebooting. He has no network configuration in his menu under preferences either. 

odd...

---

### Post by Merovius on 2008-10-27
Swapped network card and all is well. Guess it didn't like the Nvidia on board networking.

---

