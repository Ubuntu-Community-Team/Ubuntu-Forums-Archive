---
title: "Netgear router DG834G v3"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by brightspark on 2007-09-25
I have a Netgear834G router which I cannot configure with Ubuntu. Bigken suggested ndiswrapper has to be installed to make the router work.Sounds the right way to go, I have googled ndiswrapper but there does not seem to be a file that works with with the 834G. Can anyone tell me which other netgear file will work with the 834 that I can download from the ndiswrapper web site ?
Many thanks for any help,

---

### Post by vanadium on 2007-09-25
You do not need ndiswrapper to work with a router. You might need ndiswrapper to get some wireless cards that have proprietary drivers to work under Ubuntu. Your wireless card will be listed in the output of either lspci or lsusb if it is an usb card.

---

