---
title: "network interface identification and labelling"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by dk_ca on 2006-08-15
i have multiple network cards (1 wired onboard, 1 wireless, 2 wired) on Ubuntu 6.06 with latest updates.

when i configure them a certain way (one of the 2 wired cards disabled), after a reboot the interfaces get relabelled so it tries to use the wrong (disabled and unplugged) card among the 2.

Q: is there a way to make sure a specific card gets a specific label (eth0, eth1), preferrably according to the MAC address?

---

### Post by dk_ca on 2006-08-16
using /etc/iftab to associate interfaces with mac addresses did the trick.

various solutions described in:
[http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames](http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames)

---

