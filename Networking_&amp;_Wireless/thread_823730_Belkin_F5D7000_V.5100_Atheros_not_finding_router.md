---
title: "Belkin F5D7000 V.5100 Atheros not finding router"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by ghostandmachine on 2008-06-09
I have a Belkin Wireless G Desktop PCI F5D7000 v.5100 installed using Hardy. I have the Atheros Hardware Access Layer (HAL) and Support for Atheros 802.11 wireless LAN cards in use under the Hardware Devices. In the nm it shows my wireless card but once I enable it and look for my router nothing is shown.

In the hardware support components it says that my card should run out of the box under dapper and edgy. [link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin")

Any help would be great for all the message board searching I do if for a different version of the Belkin that runs a BCM chipset.

---

### Post by ghostandmachine on 2008-06-10
so I downgraded to gusty to see if that would fix the problem. it didn't. But for some reason I had the idea to manual type in the essid of the router i was trying to get into. and it worked. But now I'm curious as to why it didn't read my router in the properties of the network manager?

*edit* after connecting to my router, I went back into the nm and saw the other wireless routers in the area under the ESSID dropbox. Still it doesn't make any sense to me.

---

