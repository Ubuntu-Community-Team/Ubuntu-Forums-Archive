---
title: "Linux and NetGear WNA1000M"
date: 2019-08-09
forum: Networking &amp; Wireless
---

### Post by keramxd on 2019-08-09
Hello,
I have an issue with [COLOR=#000000]NetGear WNA1000M on Ubuntu.
I spent a lot of hours on forum and interent, tried a few tutorials, your advices and nothing helped.

I tried these:
[/COLOR][https://ubuntuforums.org/showthread.php?t=2251402](https://ubuntuforums.org/showthread.php?t=2251402)
with rtl8192 fixes
blacklist

Currently when I type:
lsusb - I see my [COLOR=#000000]NetGear WNA1000M
[/COLOR]lsmod | grep rtl - I see nothing
iwlist wlan0 scan - wlan0     No scan results

Please help me :D

---

### Post by praseodym on 2019-08-10
Please show the output of "lsusb"

---

### Post by keramxd on 2019-08-10
> **praseodym said:**
> Please show the output of "lsusb"

```
[COLOR=#FFFFFF][FONT=&quot]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT][/COLOR]Bus 003 Device 006: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8
188CUS]                                                                        
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub                 
[COLOR=#FFFFFF][FONT=&quot]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/FONT][/COLOR]
```

Sometimes I have to change USB port to make it visible in lsusb.

---

### Post by praseodym on 2019-08-10
Normally this device loads two drivers, blacklist the old one
```

echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/blacklist-rtl8192cu.conf
```
Reboot

---

