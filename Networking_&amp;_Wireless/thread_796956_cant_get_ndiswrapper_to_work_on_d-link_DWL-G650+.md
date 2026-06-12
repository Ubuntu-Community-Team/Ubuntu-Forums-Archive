---
title: "cant get ndiswrapper to work on d-link DWL-G650+"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Warpedflash on 2008-05-16
i have recently had to change my wireless card to sue my old one getting crushed. I was given a old D-link Airplus DWL-G650+ my a friend to use as his new laptop has built in wireless and he has no use for it.
i am using 7.10 on a IBM Thinkpad T21
i have installed ndiswrapper and the correct driver for the card but ubuntu wont use it.
```
rowan@rowan-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 09
       serial: 00:10:a4:78:68:b0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.0.9 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:80:c8:2e:f0:a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+

```
for some reason ubuntu insists on using the driver acx_pci. i tried
```
rowan@rowan-laptop:~$ modprobe -r acx_pci
FATAL: Module acx_pci not found.

```
as it was suggested in another thread but it says the module is not found so i cant remove it and set the windows driver to be used.

Any help is greatly appreciated
Thanks
Warpedflash

extra stuff that may be useful.
```
rowan@rowan-laptop:~$   ndiswrapper -l
gplus : driver installed
        device (104C:9066) present (alternate driver: acx)

```

---

### Post by Ayuthia on 2008-05-16
> **Warpedflash said:**
> 
extra stuff that may be useful.
```
rowan@rowan-laptop:~$   ndiswrapper -l
gplus : driver installed
        device (104C:9066) present (alternate driver: acx)

```

Have you tried to remove acx?

---

