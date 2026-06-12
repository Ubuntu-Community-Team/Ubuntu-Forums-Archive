---
title: "How to get restricted drivers back"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by DerekdeClercq on 2008-07-23
When I first installed Hardy I simply could not connect to any secured network using the restricted drivers it installed. My solution was to then install NDISWRAPPER and use it that way, which was fine for my home network but I could never get a connection to the office LEAP setup. Having made the plunge to Intrepid I would like to give the restricted drivers another go. My question is how would I go about getting the restricted drivers back. On Hardy I removed the NDISWrapper and tried to click enable again on the hardware menu under administration but it always disabled them when I rebooted. Now the atheros drivers does not even show up. I have removed the ndiswrapper package thinking it might be blocking it but I still dont get it back.

Any advice would be greatly appreciated.

---

### Post by MrSootentai on 2008-07-23
I am having a very similar problem, is there anyone here who can explain how to remove the NDISWRAPPER completely and start off with the restricted driver??

---

### Post by gpredrag on 2008-07-23
I have tried ndiswrapper with my b43, but reverted back to regular linux drivers.
To revert back from ndiswrapper I had to stop blacklisting b43 and ssb (in /etc/modprobe.d/blacklist file), AND remove /etc/modprobe.d/ndiswrapper file. Removed file sets pci aliases for wireless cards and it's used by ndiswrapper kernel module. If that file exists, ndiswrapper kernel module is loaded instead kernel modules for my wireless card (b43 in my case). 

So it's not same card, and I don't know what changes have you made trying to set ndiswrapper, but maybe this help.

---

