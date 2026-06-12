---
title: "Another Realtek 8139 post (Gutsy)"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by Aztek on 2008-03-28
Hi, I looked at some of the numerous other posts with people having problems with this NIC chipset and my situation isn't the same. I tried the pci=noapci to no avail and I am not dual-booting with Windows so the WOL issue is also out. I'm using this card:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833180004]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833180004")

Ironically I bought it because the review comments say it works in Linux. I'm sure it does but not yet ;)

Anyways, the light is on on the NIC, but I can't connect to the internet or get an IP from my router. The eth0 in the ifconfig below IS NOT the card in question. That's my old card I'm replacing. Apparently they are similar models (maybe this is causing a driver issue) When I removed the old one and put in the new one it didn't work. I put the old one back in so I could debug. Even when I have the old one out, the new one comes up as eth1 instead of eth0. I'm still pretty new to Linux and confused.

EDIT: BTW this is running on an Ubuntu 7.10-based "distro" called Restore-backup which is a backup server OS. Link below

[http://www.restore-backup.com]("http://www.restore-backup.com")

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:F4:1F:16:F8  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe1f:16f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3157516 (3.0 MB)  TX bytes:624528 (609.8 KB)
          Interrupt:16 Base address:0x4c00 

eth2      Link encap:Ethernet  HWaddr 00:08:54:A4:CC:5F  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967170 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth2:avah Link encap:Ethernet  HWaddr 00:08:54:A4:CC:5F  
          inet addr:169.254.7.168  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5853 (5.7 KB)  TX bytes:5853 (5.7 KB)

```

EDIT: lsmod...

```

 lsmod | grep 8139
8139cp                 25088  0 
8139too                27776  0 
mii                     6528  2 8139cp,8139too

```

EDIT: dmesg...

```

dmesg | grep 8139
[   31.867167] 8139too Fast Ethernet driver 0.9.28
[   32.638674] eth0: RealTek RTL8139 at 0xe0920000, 00:08:54:a4:cc:5f, IRQ 18
[   32.638677] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   32.639007] eth1: RealTek RTL8139 at 0xe0814c00, 00:40:f4:1f:16:f8, IRQ 16
[   32.639009] eth1:  Identified 8139 chip type 'RTL-8139C'
[   32.641257] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

```

---

### Post by dstew on 2008-03-29
Something doesn't add up. Your dmesg output shows the two cards as being connected on the eth0 and eth1 interfaces. The ifconfig output does not show eth1. And, the hardware address of the eth1 interface in dmesg is the same as the hardware address of the eth0 interface in ifconfig. Is this dmesg output from the same boot as the ifconfig output?

---

