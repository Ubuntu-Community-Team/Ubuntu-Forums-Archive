---
title: "Generic wireles driver"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by IceCoder on 2007-05-23
Hi, I've just installed ubuntu 7.04 server on my pc equipped with an hamlet wireless card.

i saw the wi-fi card list, and mine is not included, so I would like to know if is there any generic wireless driver to help me.

thank you.

---

### Post by chili555 on 2007-05-23
> if is there any generic wireless driverNo, sir. The chipsets used in wireless devices vary widely.

Please, with the card installed, give us a bit more information:```
lspci -v | grep Network
sudo lshw -C Network
lsusb
```Thanks.

---

