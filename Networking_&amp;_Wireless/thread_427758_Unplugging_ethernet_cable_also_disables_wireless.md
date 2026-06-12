---
title: "Unplugging ethernet cable also disables wireless"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by wareagle on 2007-04-29
I just upgraded to Feisty and started having this problem.  Is it a known issue?  As soon as I plug an ethernet cable in, everything starts working again.

Ethernet card is an Intel Pro/100 PCI
Wireless is a Buffalo WLI-PCI-G54 (Broadcom, probably using ndiswrapper, but it was detected by ubuntu during the installation).

---

### Post by wareagle on 2007-05-11
Bump...

Also, if I set my wireless card (eth1) to use monitor mode (sudo iwconfig eth1 mode Monitor), my ethernet card (eth0) quits working as well.  It retains its IP address, even if I do ifdown/ifup, but I can't ping it or get online with it.

:confused:

---

### Post by wareagle on 2007-05-22
Well, I think I figured something out.  It appears that if I disconnect the ethernet cable, Ubuntu still thinks it's connected because it retains its IP address when I run ifconfig.  Strange...

---

