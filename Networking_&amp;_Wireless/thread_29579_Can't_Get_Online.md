---
title: "Can't Get Online"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by Joe on 2005-04-24
I'm trying to get an internet connection using a Netgear WG311 wireless pci card and can't seem to pick up an internet connection.  The drivers are installed and the card is detected, I entered in my network specs and all but the only problem is that I can't seem to pick up an IP address from my router.  Anyone have any ideas?

---

### Post by alastair on 2005-04-25
There's a standard set of information people need to diagnose this type of thing.

Relevant logs from /var/log/syslog - showing device discovery/module load etc.

ifconfig -a
iwconfig
route -n

syslog logs from attempts at getting an IP address etc.

Please check the forum's archives - plus also check for specific issues with your card.

---

