---
title: "No internet connection - wired and wireless"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by mudzereli on 2008-07-28
I just did a fresh install on a laptop of mine of the newest version of ubuntu on the site, and I'm unable to connect to the internet. I've tried through the router and directly through the modem both. I've checked some threads and tried some of the solutions as far as problems that other people have had. I'm unable to ping out, and I get no dhcpoffers. Please help me out, Thanks!

---

### Post by superprash2003 on 2008-07-28
please give the following outputs from the terminal
ifconfig
iwconfig
lshw -C network

---

### Post by mudzereli on 2008-07-28
**ifconfig**
```
eth0   Link encap:Ethernet  HWaddr 00:1b:24:2c:ff:36
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
       Interrupt:16 Base address:0xa000

lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING  MTU:16436 Metric:1
       RX packets:132 errors:0 dropped:0 overruns:0 frame:0
       TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:6792 (6.6 KB) TX bytes:6792 (6.6 KB)
```

**iwconfig**
```
lo     no wireless extensions.

eth0   no wireless extensions.
```

**lshw -C Network**
```
*-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id:0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
*-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id:2
       bus info: pci@0000:08:02.0
       version: 10
       serial: 00:1b:24:2c:ff:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

---

### Post by Iowan on 2008-07-28
Contents of **/etc/network/interfaces**?

---

### Post by superprash2003 on 2008-07-29
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

