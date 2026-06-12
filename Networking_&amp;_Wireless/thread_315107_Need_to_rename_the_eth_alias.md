---
title: "Need to rename the eth alias"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by 314 on 2006-12-08
i need to rename my eth alias

right now i have 2 nic's

eth0
eth1

but eth0 is the pci card 
eth1 is the intergreated card

but i want the pci card to be eth1 
and the eth0 to be intergreated

i am using edubuntu any help is apprecied

---

### Post by FrodoB on 2006-12-08
Edit /etc/iftab and swap the names eth0 and eth1 and reboot:

sudo gedit /etc/iftab


File contents:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0a:7c:e4:ea:34 arp 1
eth1 mac 00:03:f1:70:ed:55 arp 1

change to this as an example:

eth1 mac 00:0a:7c:e4:ea:34 arp 1
eth0 mac 00:03:f1:70:ed:55 arp 1

---

