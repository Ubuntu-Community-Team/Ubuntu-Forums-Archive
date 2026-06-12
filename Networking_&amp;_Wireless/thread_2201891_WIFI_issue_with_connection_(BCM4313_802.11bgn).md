---
title: "WIFI issue with connection (BCM4313 802.11bgn)"
date: 2014-01-26
forum: Networking &amp; Wireless
---

### Post by Boris_Vujicic on 2014-01-26
HI,

I have installed ubuntu 13.10 on my Dell n5010, and for some reason i cant connect to WIFI. WIFI seems to be functioning and i can connect to some networks that i get from home but i cant connect to my home network. 
Router is D-Link GO_RT_N300 but i dont think that it has anything to do with the router since i can connect to hotspot over my phone.

---

### Post by praseodym on 2014-01-26
Download this file and save it in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
```

---

