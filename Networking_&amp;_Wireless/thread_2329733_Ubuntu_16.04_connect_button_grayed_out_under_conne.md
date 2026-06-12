---
title: "Ubuntu 16.04 connect button grayed out under connect to hidden wifi networks"
date: 2016-07-04
forum: Networking &amp; Wireless
---

### Post by mtbdrew on 2016-07-04
Fresh clean install of Ubuntu 16.04 with all updates done. Strange situation occurs after creating wifi connections to wifi network that does not broadcast SSID. After network connections are created successful when attempting to then select either of them the "connect" button is then grayed out. however, if I disable and re-enable networking the connection with then connect to one of the previously created wifi connections.

---

### Post by mtbdrew on 2016-07-18
Is no one else seeing this issue on their laptops?

---

### Post by er.magrawal on 2016-07-22
Yes,

---

### Post by mtbdrew on 2016-08-15
Anyone got a suggestion on why this is doing this in 16.04? Any work arounds?

---

### Post by wildmanne39 on 2016-08-15
Can you connect to and use wifi with hidden ssid turned off? You know that hiding your network is not anymore secure then not having it hidden and ubuntu does have more trouble with hidden connections.

---

### Post by g-moloney on 2017-02-14
If you go to bug report [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1542733](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1542733) , read / follow Frédéric's comments #32 & #34 (Start on #34 first), this will resolve the problem until the Ubuntu developers apply these patches.

Cheers.

---

