---
title: "persistent acx_pci woes"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by MrCheese on 2005-11-26
I have in my /etc/modprobe.d/blacklist file the following line :

blacklist acx_pci

as I use ndiswrapper to drive my cheapie Ti ACX111-based wifi card. However, the acx_pci module is still loading at boot.  Interestingly, dmesg shows that ndiswrapper is now loading first. Can anyone shed any light on why acx_pci is still loading & how to stop it please?

MrCheese

Edit - duh! I just discovered /etc/hotplug.d/blacklist, popped acx_pci in there & am now up & running at boot.

---

