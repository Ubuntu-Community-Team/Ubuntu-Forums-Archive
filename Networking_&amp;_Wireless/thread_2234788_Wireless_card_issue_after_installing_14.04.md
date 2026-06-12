---
title: "Wireless card issue after installing 14.04"
date: 2014-07-16
forum: Networking &amp; Wireless
---

### Post by vitaly3 on 2014-07-16
Hey guys, got a macbook pro, wireless card is :
Multimedia controller [0480]: Broadcom Corporation Device [14e4:1570]
    Subsystem: Broadcom Corporation Device [14e4:1570]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)

what steps should I take from here? I've read up a bit and it seems to be a pretty common issue.

Thanks in advanced guys.

---

### Post by Hadaka on 2014-07-16
Hi please post the output of  ..
```
uname -a
lspci -n | egrep '0200|0280'
```
thanks

---

