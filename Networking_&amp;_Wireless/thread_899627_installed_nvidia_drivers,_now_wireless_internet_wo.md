---
title: "installed nvidia drivers, now wireless internet won't work...."
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by ferno on 2008-08-24
OK, so I installed a new graphics card in my PC, and then installed the drivers from nVidia (because the restricted drivers weren't working) and now when I start up Ubuntu my wireless internet doesn't work at all, i don't think my network adapter (its a dynex pci wireless adapter from best buy) is even being recognized... 

My wireless was working perfectly before (out of the box without any configuration), but now it doesn't...

The only thing I did was boot into safe mode, change to runlevel 3, and install the nVidia drivers, then I rebooted and my video works fine, but my wireless is just shot..


when i type iwconfig i get:

lo     no wireless extensions

eth0   no wireless extensions


and with lspci, this is the line with my network adapter:

Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)


any ideas on what could of went wrong and how i can fix it? thanks.

---

