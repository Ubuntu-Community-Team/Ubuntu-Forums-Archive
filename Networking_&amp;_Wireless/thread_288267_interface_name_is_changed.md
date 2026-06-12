---
title: "interface name is changed?"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by forbmj on 2006-10-29
I have two wireless cards. When I tried to install rtl8180 driver for one card, it changed the interface name of my second card from eth1 into eth2. How can I change it back because I don't use this rtl8180 card any more? It's quite annoying when I have to use eth2, but after resuming from suspend the system tried to bring up eth1.

Thanks a lot.

---

### Post by pdub on 2006-10-29
You can change the names by editing iftab

Make a backup first:

**sudo cp /etc/iftab /etc/iftab_bak**

**sudo gedit /etc/iftab**


you can remove the old wireless adapter and then change the interface name back to eth1 for the other card.

May require a reboot or at least a retart of networking:

**sudo /etc/init.d/networking restart**

This is how I have done this in the past, not sure if there is a better way.

---

