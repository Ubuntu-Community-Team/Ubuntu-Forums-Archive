---
title: "Broadcom Gigabit PHYSICAL Problem"
date: 2005-11-29
forum: Networking &amp; Wireless
---

### Post by plueken on 2005-11-29
I have three network adapters.  My primary one is a Broadcom Corporation NetXtreme BCM5705 Gigabit Ethernet (rev 01).  This works fine in Windows and continues to work fine, so there is no problem with the physical card itself.  It also has about a 10% chance of loading fine when Ubuntu loads, but it's the other 90% of the time that is a problem.

During the boot screens, the system halts for several seconds when checking for networking capabilities.  Later on, the system fully recognizes eth1 (an old onboard 10/100 connection and my current backup) and ath0 (my wireless), but most of the time it will not acknowledge eth0 at all.  In the Device Manager, I can look up the Broadcom card, and it has all of the specs accurately, but it simply won't recognize its networking capabilities.

I've updated drivers and tried many other tweaks, but I think the problem is deeper.  I tried the basic "sudo mii-tool eth0" command, and it returns 
"SIOCGMIIPHY on 'eth0' failed: No such device".  The machine simply doesn't recognize that there is a network connection through that card at all.

Does anyone have any possible suggestions at all?  Thanks in advance.

- Plueken

---

