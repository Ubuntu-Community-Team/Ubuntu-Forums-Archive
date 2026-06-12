---
title: "RTL8811au not working after update"
date: 2018-12-03
forum: Networking &amp; Wireless
---

### Post by salseng on 2018-12-03
Hi, 

I have been using the following USB wifi adapter without any issues until today:

NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]

Linux Kernel:
4.15.0-42-generic

for lsusb I have the following: 

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0489:c022 Foxconn / Hon Hai 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 1c4f:0059 SiGma Micro 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Now, after some sort of "update" I can't use the wifi adapter anymore, it says "no wifi adapter found"

Please help!

---

### Post by jeremy31 on 2018-12-04
Post results from terminal for ```
modinfo 8812au; dpkg -l | grep 8812au
```

---

