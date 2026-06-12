---
title: "Build bcmwl-kernel-source in Ubuntu 12.04.5: Required header and dkms packages"
date: 2014-12-01
forum: Networking &amp; Wireless
---

### Post by AlanCanon on 2014-12-01
Since wubi is no longer supported in Ubuntu 14.04 and above, I had to use the 12.04 Ubuntu wubi to bootstrap Ubuntu onto a laptop for which I had no other installation options. The 12.04 wubi installer doesn't install the restricted drivers for my Broadcom 43XX, and installing the packages involved prerequisites that also aren't installed automatically with the 12.04 wubi install.


I searched the package repositories until I came up with a set of packages that will do the trick, and here they are (in the order they need to be installed.)


Hope this is helpful.

bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb
dkms_2.2.0.3-1ubuntu3.2_all.deb
linux-firmware-nonfree_1.11_all.deb
linux-headers-3.13.0-36_3.13.0-36.63~precise1_all.deb
linux-headers-3.13.0-36-generic_3.13.0-36.63_amd64.deb

---

### Post by mikewhatever on 2014-12-01
There is a howto for that: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access).

---

