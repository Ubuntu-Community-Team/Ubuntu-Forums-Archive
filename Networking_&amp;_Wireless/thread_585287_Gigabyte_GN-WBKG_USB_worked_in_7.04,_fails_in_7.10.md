---
title: "Gigabyte GN-WBKG USB worked in 7.04, fails in 7.10 (editing /etc/network/interfaces)"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by dara on 2007-10-21
I found instructions for how to modify /etc/network/interfaces in order to get my wireless USB adapter working in Ubuntu (see [http://ubuntuforums.org/showthread.php?t=417145](http://ubuntuforums.org/showthread.php?t=417145)).  These instructions worked in 6.10 and 7.04 but now fail in 7.10.  I tried Network Manger as soon as I installed 7.10 but that didn't work so I uninstalled it and edited the interfaces file.  After a reboot, no luck.  I changed the name of the device in the file from rausb0 (6.10) to rausb1 (7.04) to wlan0 (7.10) based on the output of sudo lshw.

Unfortunately, my hardware is not listed on the supported cards page ([https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)) though it used to work ok and I hoped it would just get better with later releases.

If this is going to be a headache, I'm tempted to buy a PCI wireless card for $40 US or so and be done with it.  Does anyone have any advice on or link to the best other thread to get my USB hardware to work, or advice on a totally out of the box solution for PCI wireless on Ubuntu 7.10?

Dara Parsavand

---

