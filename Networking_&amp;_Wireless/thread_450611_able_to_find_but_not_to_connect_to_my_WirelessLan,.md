---
title: "able to find but not to connect to my WirelessLan, WiredLan not working at all."
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by DuKe2112 on 2007-05-21
I'm a complete newbie to Linux and just jusing a fresh Ubunru installation without much configuration done.

Its semms Ubuntu automatically detected my 56k Modem and my WLan correctly, but it wont work  and my ordinary LAN dosnt show up at all.
First off all the Hardware is OK, because under WindowsXP its just working fine.

The modem doesn't matter, because I use a router (T-Sinus 154 DSL SE, to be exact).

Now for the WLAN (RaLink 802.11g):
The System is able to detect that both My Neighbour and myself have WLan but it cant connect to it, it just tries fpr some seconds and then stops.
For testing I positioned the notebook directly next to the router and disabled both encryption an MACfilter.

For the Lan (Agere Systems ET-131x):
Ubuntu doesnt seem to even notice that I have a Lan connector. I couldn't even find it in the Hardware information of Ubuntu, although I found the WLan.

Any idea what might cause these Problems?
I dont realy care about the Lan, but could it Somehow affect the WLAN? 
I'm manly confused that the WLan works at least partly. If it is a driver Problem, shouldn't it be unable to even find the Network? And not just refuce to connect?

---

### Post by blazercist on 2007-05-21
i dunno about your wired connection, perhaps it needs a special driver... your wifi card is not working because there is a driver glitch...  is your home network encrypted with say WEP?  due a glitch in the latest beta of this driver it has a hard time remembering WEP keys and therefore it will detect the network but it doesnt authenticate and associate.  To solve this you will either need to turn off your router's WEP encryption and leave your network OPEN, or you will have to download the newest version of the driver's source code, and the patch, then patch the driver and compile and install it manually.  seeing as how you are new to linux I recommend simply turning off the encryption and password all your shared folders and resources.  its sloppy but itll work.

---

### Post by DuKe2112 on 2007-05-22
Well as I said, for testing purposes I already opened my network completely, but it helped not a bit.
I'll try if I can get a better driver working.

For the the missing lan driver: shouldn't it at least be able to detect that this driverless piece of hardware is some type of lan card?

---

### Post by DuKe2112 on 2007-05-23
Yep, found the driver but not a clue as how to install it (;

---

