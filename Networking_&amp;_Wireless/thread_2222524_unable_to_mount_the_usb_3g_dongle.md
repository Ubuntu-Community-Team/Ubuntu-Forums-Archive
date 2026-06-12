---
title: "unable to mount the usb 3g dongle"
date: 2014-05-07
forum: Networking &amp; Wireless
---

### Post by gp1232 on 2014-05-07
I am trying to run Teracom LW273 3G dongle to run on my ubuntu 13.10 (64-bit), but I am unable to do so...

I have seen a lot of links on how to install it on ubuntu, but it seems to be completely different problem

when the dongle is unplugged and i tru lsusb i get 

```
root@gaurav-Lenovo-IdeaPad-Y500:/home/gaurav# lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04f2:b331 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

after plugging the dongle and doing lsusb i get

```
root@gaurav-Lenovo-IdeaPad-Y500:/home/gaurav# lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04f2:b331 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 009: ID 230d:0101  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

now that the dongle is present, i try to switch the mode using usb_modeswitch

```
root@gaurav-Lenovo-IdeaPad-Y500:/home/gaurav# usb_modeswitch -v 230d -p 0101 -u 3

Looking for default devices ...
   found matching product ID
Getting the current device configuration ...
 OK, got current device configuration (1)
 Found device in default mode, class or configuration (1)
Accessing device 010 on bus 003 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x07 (out) and 0x87 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HSPA
   Model String: CD-ROM
Revision String: 0000
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HSPADataCard
     Product: HSPADataCardA
  Serial No.: 8444311594054030
-------------------------
Changing configuration to 3 ...
 Device is busy, trying to detach kernel driver
Looking for active driver ...
 No driver found. Either detached before or never attached
 Device is busy, trying to detach kernel driver
Looking for active driver ...
 No driver found. Either detached before or never attached
 Device is busy, trying to detach kernel driver
Looking for active driver ...
 No driver found. Either detached before or never attached
 Device is busy, trying to detach kernel driver
Looking for active driver ...
 No driver found. Either detached before or never attached
 Setting the configuration returned error -22. Trying to continue
-> Run lsusb to note any changes. Bye.


```

I can't figure out what to do next. Please help.

Thanks in advance.

---

### Post by Navneet_Kumar on 2014-05-07
i would suggest that you should install wvdial and its dependent packages and edit the /rtc/wvdial.conf file so as to enter your uname and passwd,and after then it will work fine by just running sudo wvdial fron the terminal.........:D

---

