---
title: "yet another broadcom nightmare... very strange issue"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by PixelCloud on 2006-09-15
When i first installed ubuntu, the ndiswrapper method worked for getting my broadcom wireless card working (4306. However, after the most recent kernel update, my wireless suddenly stopped working.

After hours of fiddling with the settings and trying to get it running again, i have had no success.

This is the problem.

According to ndiswrapper -l , the driver is installed and the hardware is present.

iwconfig shows my wireless card

networkmanager shows all the various wireless networks.

But connecting to them fails, everytime.

---

### Post by PixelCloud on 2006-09-15
fixed it..

i think my pci slot was broken or something...

---

