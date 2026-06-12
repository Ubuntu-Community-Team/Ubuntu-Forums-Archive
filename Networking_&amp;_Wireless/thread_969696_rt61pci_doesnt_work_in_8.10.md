---
title: "rt61pci doesnt work in 8.10"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Tichondrius on 2008-11-03
Just wanted to warn you that Ubuntu 8.10 Ibex is very buggy at least for now. It has ruined my weekend because when I installed it, I had problems with my network card. It's a GIGABYTE GN-WP01GS PCI card, and in 8.10 it was detected but it could not find any wireless networks (iwlist scan also returned empty results). Also there were some error messages about phy0 register in dmesg.
I was ready to RMA the card, but then tried installing Ubuntu 8.04 and it worked out of the box. So the card is not defective, only Ubuntu 8.10 is.
BTW, the driver for this card is rt61pci (kernel module), I guess it became broken in 8.10. And it's not a wep/wpa issue, it's that the driver is somehow broken and is getting errors while communicating with the card.

---

