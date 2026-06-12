---
title: "D-Link WUA-1340 USB Wireless - configuring rt73 driver"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by bitreaper on 2007-05-21
I'm new to linux, just getting Feisty installed for the first time, and trying to make my USB wireless adapter work. 
Ndiswrapper didn't end up working, but I found a tutorial for the ralink rt73 drivers and my adapter seems to be detected as "Wired Network (Unknown USB Vendor Specific Interface)". I'm trying to get onto my network, but I'm not sure how to properly configure my adapter. I believe I have to use iwconfig on the rausb0 device, but the man pages haven't been much use to me so far. My network is set up as follows:

essid: default
channel: 2
64 bit WEP encryption

I realize it's probably simple but I can't seem to figure it out. Any help would be greatly appreciated.

---

### Post by dannyboy79 on 2007-06-07
here's the instructions for either using ndiswrapper OR native linux drivers. [http://ubuntuforums.org/showthread.php?t=270756&highlight=WUA-1340](http://ubuntuforums.org/showthread.php?t=270756&highlight=WUA-1340)

---

