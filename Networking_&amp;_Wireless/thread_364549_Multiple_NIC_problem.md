---
title: "Multiple NIC problem"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by bleearg on 2007-02-18
Hi all,
I am working on one of my machines which has three network interfaces on it.  Each time I reboot, two of the interfaces keep switching.  More specifically, eth1 likes to swap places with eth2 and vice versa.  I remember I used to have a similar problem with Fedora/RH and could fix it by editing some kudzu file.  Is there something similar in Ubuntu?  To clarify, I'd like to nail the config for eth1 to the NIC in PCI slot X and the config for eth2 to the NIC in PCI slot Y.

Any ideas?

TIA,
eric

---

### Post by spd106 on 2007-02-18
Try editing the /etc/iftab file.

---

### Post by bleearg on 2007-02-19
Thanks very much - that did it.

---

