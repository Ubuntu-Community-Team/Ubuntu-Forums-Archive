---
title: "Cannot find/add wifi driver"
date: 2017-12-16
forum: Networking &amp; Wireless
---

### Post by acdoyle630 on 2017-12-16
I just installed Ubuntu 16.04 and cannot see wifi networks.  If I run 
```
[SUP]lsusb[/SUP]
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f3:22c3 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 0bda:58ed Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any insight would be appreciated.

---

### Post by chili555 on 2017-12-16
Please show us the result of:```
lspci -nnk | grep 0280 -A3
```

---

### Post by acdoyle630 on 2017-12-16
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    DeviceName: WLAN
    Subsystem: Hewlett-Packard Company Device [103c:8319]

---

### Post by chili555 on 2017-12-16
The well known d723. Sorry, there is no known driver.

[https://ubuntuforums.org/showthread.php?t=2367405](https://ubuntuforums.org/showthread.php?t=2367405)

[https://askubuntu.com/questions/961299/cannot-see-my-wifi-10ecd723-when-trying-ubuntu](https://askubuntu.com/questions/961299/cannot-see-my-wifi-10ecd723-when-trying-ubuntu)

---

