---
title: "change wireless rate to 1 Mb/s; opposite of normal!!"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by logis9 on 2007-12-11
My Linksys AP is currently set at 1 Mb/s in 802.11b mode, and I've verified it to do. I am running the default driver that comes with Ubuntu on my dell laptop with intel 3945abg card. Is it possible to set the card to transmit only at 1 Mb/s? If not, is there another card that only stay at 1 Mb/s?
(Right now, while the AP only transmits at 1 Mb/s, the card still transmits at 1,2,5.5,and 11).

---

### Post by edm1 on 2007-12-11
```
sudo iwconfig eth1 rate 1M
```

where eth1 is your wireless interface

---

### Post by logis9 on 2007-12-11
> **edm1 said:**
> ```
sudo iwconfig eth1 rate 1M
```

where eth1 is your wireless interface

This worked great. Thanks!!!!

---

