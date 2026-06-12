---
title: "Not detecting my Wireless USB :["
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by indianboy603 on 2008-07-14
So my Ubuntu comp was working fine and dandy until yesterday...
I accidentally kicked my power cable which caused it to restart and now the network manager isn't detecting my USB Wireless card. 

Here is my "lshw -C network":
```
*-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:16:76:6b:64:4c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

```

"lsusb":
```
Bus 004 Device 002: ID 0bc2:0503 Seagate RSS LLC 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 002 Device 002: ID 0425:f102 Motorola Semiconductors HK, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

"iwconfig":
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

I've been searching forever and i can't figure it out. This is not due to the recent updates. I think it lost the address of the USB or something. Is there a way to rescan the USB ports?

Thanks,
indianboy603

---

### Post by indianboy603 on 2008-07-19
Any help?? :mad:
or do i just use Win XP instead?
cuz that actually works...

---

