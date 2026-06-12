---
title: "Hotspot in 16.04 - change band to N/5GHz?"
date: 2017-07-02
forum: Networking &amp; Wireless
---

### Post by Nisuspi on 2017-07-02
I've got an Ubuntu box which is working part time as a wifi hotspot (basically as a VPN gateway). 

It's up and working using this set-up method: [http://learn.linksprite.com/project/create-wifi-hotspot-in-ubuntu-16-04-android-support/](http://learn.linksprite.com/project/create-wifi-hotspot-in-ubuntu-16-04-android-support/)

Does anyone know how to turn it into a 5GHz or 802.11n network? At the moment it only seems possible to create [a|bg] networks using the default tools.

---

### Post by praseodym on 2017-07-02
Depends on the driver you are using. Check "iwlist chan"

---

### Post by Nisuspi on 2017-07-02
That gives me a list of 11 channels in the 2.4Ghz spectrum as capabilities. According to 'lshw -C network' the driver is 'bcma-pci-bridge', wireless- IEEE 802.11bgn.

I did change the driver from the kernel to the b43 driver to get the hotspot working at all iirc. Will try switching back.

---

