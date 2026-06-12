---
title: "ralink 3070 enable problem"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by rimi on 2010-09-26
Hi,
     Recently I tried to use wireless connection with Ralink 3070 in ubuntu in my dell 1520 vostro as the inbuilt bcm4312 does not connect to wireless connection. But installing Ralink 3070 (used as external usb) is also unable to connect to wireless connection as the I think the two driver are in conflict. Please help regarding this.

---

### Post by cariboo on 2010-09-28
I've got a BCM4312, that works just great, all you need to do is install the restricted drivers. Depending on what version it is, it uses either the STA driver or the B43 driver. To install the STA driver you need a network connection via an ethernet cable, or it can be installed using the Live CD, You will need to install build-essentials first if you need the sta driver. Build-essential and bcmwl-kernel-source are located in the pool directory on the Live CD.

---

