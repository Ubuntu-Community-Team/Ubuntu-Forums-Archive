---
title: "Problem with linksys wireless G"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by ComputerPsi on 2007-05-16
I posted this on the absolute beginners area, but I guess it doesn't fit there..

Hello all. I use to have a USB linksys wireless b and it worked on Ubuntu.. then I went back to Windows. Now I have a USB linksys wireless G router and I put back my version of Ubuntu. The system didn't seem to detect the device at all. I have Ubuntu version 6.06. I didn't find a driver anywhere. Does anybody know a quick solution? (When I plug in my old broken wireless B, ubuntu gives an option to use it. When I plug in my new wireless G, ubuntu does nothing.) I have a compaq desktop pentium III.

Thank You,
ComputerPsi

---

### Post by chili555 on 2007-05-16
Please tell us more about your wireless adapter. Plug it in and then do, in a terminal:```
sudo lshw -C network
lsusb
```Please post the result here. Thanks.

---

### Post by ComputerPsi on 2007-05-16
Here is the result:

venia@venia:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 01
       serial: 00:02:a5:02:b1:61
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:40000000-40000fff ioport:1000-103f irq:193
venia@venia:~$ lsusb
Bus 001 Device 002: ID 13b1:0020 Linksys
Bus 001 Device 001: ID 0000:0000

---

### Post by Kobalt on 2007-05-16
According to your lsusb, your wifi stick seems to be a WUSB54G. Check [this]("https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC") out in order to get it working. If it doesn't work, search the forums since there are many threads on how to get it working...

---

