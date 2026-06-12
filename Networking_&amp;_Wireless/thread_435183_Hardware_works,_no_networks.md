---
title: "Hardware works, no networks"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by ccw127 on 2007-05-06
I am trying to connect to my wireless AP under feisty but I can't find any available networks. I know it is not the AP because I have tried three different ones (one of which I reset to defaults. I also know that feisty detected the pci wireless card:

lspci -v (pertinent info...):

07:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Subsystem: Linksys Unknown device 0014
Flags: bus master, fast devsel, latency 32, IRQ 20
Memory at 90004000 (32-bit, non-prefetchable) [size=8K]

I also tried to set up the link manually but to no avail.

HELP

This is for a friends computer that I have finally convinced to switch to linux, but no wireless when that is the only choice where he lives is kind of a make or break situation.

Chris

---

### Post by josephus on 2007-05-06
the driver is probably not loaded properly.  the drivers that come with ubuntu for broadcom cards don't have the necessary firmware to drive the card.  you need to either use fwcutter to extract the firmware or use the windows drivers + ndiswrapper to get your card going.

try following this 

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

or this

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

### Post by ccw127 on 2007-05-06
Thank you, as soon as I get the system installed I will try the directions on the 2nd linked post. I was initially running in 'live' mode because I didn't want to install if i couldn't get all the hardware to work so I am not going to bother until it is a permanent install.
I will post the results (success or failure) as soon as I finish.

Chris

---

### Post by ccw127 on 2007-05-08
That did it. Working great now.

Thanks,
Chris

---

