---
title: "Ubuntu 16.04 with Tplink T9E 1600AC"
date: 2017-04-10
forum: Networking &amp; Wireless
---

### Post by waloshin on 2017-04-10
How do I get my Tplink T9E working? I do not have access to ethernet right now.

---

### Post by chili555 on 2017-04-11
This thread suggests that it's a Broadcom supported by the driver wl. [https://ubuntuforums.org/showthread.php?t=2349005](https://ubuntuforums.org/showthread.php?t=2349005)

Confirm:```
lspci -nnk | grep 0280 -A2
```You can get the driver from the installation USB or DVD like this: [http://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619](http://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619)

As always, post back if you get stuck.

---

