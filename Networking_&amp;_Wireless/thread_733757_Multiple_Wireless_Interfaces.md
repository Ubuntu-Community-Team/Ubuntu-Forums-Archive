---
title: "Multiple Wireless Interfaces"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2008-03-24
Dear, 

How to run multiple Multiple Wireless Interfaces (Let say 2 interfaces simultaneously). What should I do? Compiling the new kernel or installing a new kind of network manager?

Please assist.

---

### Post by SpaceTeddy on 2008-03-24
i don't think you need a different kernel.
the standard network manager does not support network connections on more than one device - which means you will have to configure the second one in the console... or use a different network manager (which i do not know... i always do it thought the CLI)...

a good start are the commands iwconfig (configuration of wireless network cards), ifconfig (general configuration of any network card) and dhclient (getting eases from dhcp-servers).

normally what i would do is use iwconfig to attach the wireless card to a network, and then either use dhclient to get an ip, or use ifconfig to set myself a static ip... 

hope it helps...

---

