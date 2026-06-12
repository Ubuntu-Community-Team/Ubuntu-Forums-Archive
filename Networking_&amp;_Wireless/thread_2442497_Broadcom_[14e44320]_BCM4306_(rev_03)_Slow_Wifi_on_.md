---
title: "Broadcom [14e4:4320] BCM4306 (rev 03) Slow Wifi on Ubuntu Server 20.04"
date: 2020-05-04
forum: Networking &amp; Wireless
---

### Post by roughlea on 2020-05-04
Hi,

I am am experiencing slow wifi for a 
Linksys WMP54GS v1.0 wireless PCI card with Ubuntu Server 20.04
installed, e.g. apt-get has taken 18 minutes 41 seconds to fetch 459Kb.

Following the advice from [here]("https://ubuntuforums.org/showthread.php?t=2214110"), I have installed the firmware-b43-installer
package. The card is recognised and allocated an IP. However, it is very slow.
Posting here in the hope that somebody can help. As shown in the 
system log information below the b43-pci-bridge is showing messages concerning
 swiotlb buffer is full.

Using the [wireless-info]("https://ubuntuforums.org/showthread.php?t=370108") tool the wireless system configuration is available at:
[URL="https://pastebin.com/aUhd35m7"]
https://pastebin.com/aUhd35m7[/URL]

Has anybody managed to get the Linksys WMP54GS v1.0 card working
on Ubuntu Server 18.04.4+ using b43 drivers or ndiswrapper?

---

