---
title: "[SOLVED] MadWiFi linux restructed wda 2320 or AR5212 802.11 abg."
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-18
This os is Feisty.

I thought I had removed and reinstalled

linux-restricted-modules-2.6.20-16-386

and that this would find the D-Link WDA 2320 card. It didn't.

I did a locate linux-restricted-modules-2.6.20-16-386 and saw:

/var/cache/apt/archives/linux-restricted-modules-2.6.20-16-386_2.6.20.5-16.29-i386.deb

is this correct?

a locate madwifi

shows about a dozen lines, all of them in /lib/modules/2.6.20-15-generic/madwifi

so does this mean that if the card is good, the pci bus should have detected it?
That is, is this enough or is there other software that needs installing?

---

### Post by Mark_in_Hollywood on 2007-07-20
Card was bad has been replaced. lspci shows it as on the bus.

thanks.

---

