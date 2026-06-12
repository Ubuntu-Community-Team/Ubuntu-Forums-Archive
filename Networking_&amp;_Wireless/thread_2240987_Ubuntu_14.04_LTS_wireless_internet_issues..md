---
title: "Ubuntu 14.04 LTS wireless internet issues."
date: 2014-08-23
forum: Networking &amp; Wireless
---

### Post by len4 on 2014-08-23
umm, hi... im new to using Ubuntu, and i have ubuntu 14.04 LTS, my  wireless internet connection drops at times and doesnt come back for a  while on some occassions. can someone help me? maybe walk me through a  way to fix this problem? it would be much appreciated.

someone said i should include this info so This is the information i got from "lspci -nn | grep 0280"


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)

---

### Post by chili555 on 2014-08-23
I believe your device uses the driver *rtl8192se*. Let's see if we can see why it's dropping from the logs:```
cat /var/log/syslog | grep -e rtl -e etwork
```Thanks.

---

