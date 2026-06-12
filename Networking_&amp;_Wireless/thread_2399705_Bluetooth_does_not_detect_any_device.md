---
title: "Bluetooth does not detect any device"
date: 2018-08-28
forum: Networking &amp; Wireless
---

### Post by egilaren on 2018-08-28
Hi, my bluetooth does not deted any device. All my friends can, but mi Ubuntu 18.04.1 LTS. any idea to solve it? Thanks.

Details of my pc:
Broadcom BCM943142Y
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)

---

### Post by mIk3_08 on 2018-08-29
Try to install bluetooth manager in your system.
Maybe it will help.

---

### Post by jeremy31 on 2018-08-29
Post results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```
It is likely missing firmware

---

