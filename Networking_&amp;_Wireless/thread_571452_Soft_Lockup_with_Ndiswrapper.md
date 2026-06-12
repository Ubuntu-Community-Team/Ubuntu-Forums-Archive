---
title: "Soft Lockup with Ndiswrapper"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by Ox1GeN on 2007-10-09
I have some troubles with my wireless card.. (D-Link g520m)
I've installed ndiswrapper, installed drivers, blacklisted ath_hal and ath_pci (as it was written in HOWto) and rebooted..
Everything worked well until the second reboot..
It is locking up on the loading screen. I've tried the recovery mode and there i've got smth like that:

*Configuring network interfaces...
[some numbers] BUG! Soft Lockup on CPU#0.

It's clear that the problem is in ndiswrapper.
Help plz!!:(
P.S. I can boot Ubuntu with unplugging Wi-fi card.. So that's it..

---

### Post by kevdog on 2007-10-09
So boot without the network card

Then when your in -- uninstall the drivers associated with ndiswrapper

sudo rm -rf /etc/ndiswrapper/*

Also remove the statemtent ndiswrapper in the /etc/modules files to prevent ndiswrapper from loading at boot.

---

### Post by Ox1GeN on 2007-10-09
> **kevdog said:**
> So boot without the network card

Then when your in -- uninstall the drivers associated with ndiswrapper

sudo rm -rf /etc/ndiswrapper/*

Also remove the statemtent ndiswrapper in the /etc/modules files to prevent ndiswrapper from loading at boot.

MMmmm...
I need that card working! =) Any ideas?

---

### Post by kevdog on 2007-10-09
Yea, but lets get it so you can boot with the card in place and then we can troubleshoot ndiswrapper.

When booting with the card in place can you post
ndiswrapper -v
ndiswrapper -l
lspci -nn
lshw -C network

---

