---
title: "Broadcom BCM4352 Wireless [14e4:43b1]-Works on 18.04 Live CD but not after installed"
date: 2018-05-20
forum: Networking &amp; Wireless
---

### Post by evan02 on 2018-05-20
Able to get this work while on the Live CD simply by running apt install bcmwl-kernel-source - with out even running an update first.

But after actually installing 18.04 I am unable to get any sort of wireless connectivity. Even after connecting a wire and apt updating.

Here is the output of the wireless-info script: [http://paste.ubuntu.com/p/nbdJfNy4rJ/](http://paste.ubuntu.com/p/nbdJfNy4rJ/)    --(while on live cd)

Any help would be greatly appreciated.

---

### Post by evan02 on 2018-05-20
Welp - its now working.

All I did was re-run the install. I got wifi working from the Live-CD and ran the installer with out rebooting in between and made sure to check boxes to check for updates and install third party drivers while installing.

---

