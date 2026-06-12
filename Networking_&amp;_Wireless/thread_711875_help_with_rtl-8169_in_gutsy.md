---
title: "help with rtl-8169 in gutsy"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Peter09 on 2008-03-01
I have persuaded my son to go with Ubuntu. Yesterday (over the phone) I helped him install it. Initially he did not get a network connection but we fixed that, it was a Bios problem, the on-board LAN was disabled.

This morning when he boots the machine he has no network connection. The O/S does not see his network card, although it is recognized in the hardware listing.

The card is shown as a rtl-8169. What things to do to get this working.? I guess there must be a driver present because it was working yesterday. Network manager just shows a modem connection.

PC

---

### Post by jhetrick62 on 2008-03-01
Honestly, that family of wireless chips has been very flaky on Linux drivers.  Follow Kevdog's howto and install ndiswrapper, built the driver from winxp driver and blacklist your current driver.

This should work just fine.

Jeff

---

