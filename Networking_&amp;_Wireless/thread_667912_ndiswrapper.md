---
title: "ndiswrapper"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by dmaksimov on 2008-01-14
so i followed the guide to install my wpnt121 on gusty, well everything worked ok to install driver and stuff until the "sudo ndiswrapper -m" command. it said :

module configuration contains directive install usb:v1385p6E00d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 868, <MODPROBE> line 409.
module configuration already contains alias directive

anyone know whats up?

---

### Post by HermanAB on 2008-01-14
Hmm, no clue.  Go to ndiswrapper.sourceforge.net.

Cheers,

Herman

---

