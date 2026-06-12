---
title: "Bcm 4306 Wireless Card Problem"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by asonetuh on 2008-01-09
My wireless card (bcm 4306) worked fine under feisty, but I've had problems getting it working under gutsy. I used the GTK installer for the bcm 43xx to install the firmware, and that was successful. Under the restricted drivers manager, it now says that the firmware is in use. However, my wireless card isn't able to detect any networks (its on roaming mode). When I use the "lshw -C network" command, it outputs the following:

*-network:1 DISABLED
description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN controller

plus a bunch of other card information.

I'm just a beginner with using Linux, so any help from the community would be greatly appreciated!

Cheers,
asonetuh

---

### Post by lonniehenry on 2008-01-09
To fix your wireless, unenable restricted driver for broadcom, and then follow the following link [http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902")
 It will install the ndiswrapper and work well.  I have been using it on a new gutsy installl and worked when other methods didn't.  Good luck.

---

