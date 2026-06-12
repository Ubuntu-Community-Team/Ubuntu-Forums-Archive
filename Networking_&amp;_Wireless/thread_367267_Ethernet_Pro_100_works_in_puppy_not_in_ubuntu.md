---
title: "Ethernet Pro 100 works in puppy not in ubuntu"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by elev on 2007-02-21
I cannot get my ethernet connection to work.. DHCP doesn't work, static addresses don't work.  I've edited my ect/network/interfaces file.  The worst part is, is that the NIC works great in Puppy and DSL, but not in Ubuntu.  Is this a driver issue?

*edit*
I read about the "noapic" option from installation.  Is there a way I can take advantage of without reinstalling?

---

### Post by gradedcheese on 2007-02-22
Hmm... post your "lspci" output (the lines starting with "Ethernet Controller") so that we know what chipset that NIC has exactly.  I assume that the interface shows up (as eth0 or something) but it's just the rest of this stuff that doesn't work?

---

