---
title: "PS3 Networking not working.  Psubuntu sent me here."
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by bobbob1016 on 2007-02-22
Here is my post on Psubuntu's forums: [http://psubuntu.com/forum/viewtopic.php?p=73#73](http://psubuntu.com/forum/viewtopic.php?p=73#73)

To give an overview, I have Kubuntu on my PS3 (which I am going to switch to ubuntu), but I am unable to get the network connected to "aptitude install ubuntu-desktop".  I am in the System Settings for the Network, I clicked Administrator Mode, then whenever I enable the ethernet, I it says enabled for a second, then switches back to disabled.  Through some looking around, we figured that I might not have networking permissions.  When I typed "ethtool eth0" it said:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
Cannot get message level: Operation not permitted
Cannot get link status: Operation not permitted
No data available

When I typed it as sudo it gave me:
Supported ports: [TP]
Supported link modes: 10baseT/Half 10baseT/Full
Same with 100 and 1000.
Advertised auto-negotiation: Yes
Speed 100Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: no
Link detected: yes 

The person who was helping me there, sent me here because he had to leave.  I'm not a newb, I am typing this on my Ubuntu desktop, and I also have Ubuntu on two laptops, I am just not sure where the problem is.  I'm not sure if it is a KDE thing I'm not seeing, or if it is some step I missed.  I've been trying for two days now.  Here are the directions I followed:
[http://psubuntu.com/installation-instructions/](http://psubuntu.com/installation-instructions/)  --I followed these
[http://ubuntuforums.org/showthread.php?t=343113](http://ubuntuforums.org/showthread.php?t=343113)  --And found these later.  They looked the same so I kept with the ones on psubuntu, incase the directions differed anywhere.

---

### Post by Ciego on 2007-02-22
I would check against the original and up to date instructions too.  FredTech copied these to the site but they are outdated and there are some mistakes/formatting issues.

[http://ubuntuforums.org/showthread.php?t=343113&highlight=ps3](http://ubuntuforums.org/showthread.php?t=343113&highlight=ps3)

---

### Post by bobbob1016 on 2007-02-22
There is nothing in those directions, as far as I see that I haven't done, as networking goes.  I'll reinstall if need be, I'd prefer not to though, because of the amount of time it takes.

---

