---
title: "[SOLVED] network-manager / networking issues"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by bmeyer on 2007-07-25
I was happily using wireless yesterday when after a few hours, network-manager completely drops my wireless connectivity.  My wireless interface (ra0) does not show up in network-manager admin anymore.  At first I thought it might be a mac address issue, but after playing around with it only seemed to make matters worse.

It's a Linksys PCI wireless card (RT61 chip).  RT61 module is blacklisted and updated driver installed with ndiswrapper.

Any ideas?

I noticed in lshw that the RT61 controller (network-1) says "UNCLAIMED".  Why does ifconfig have eth0 and eth1 duplicated with :avah?  And why doesn't ra0 show up in iwconfig?

iftab:
```
eth0 mac 00:04:75:a1:0f:dc arp 1
eth1 mac 00:0c:76:97:f2:df arp 1
ra0 mac 00:18:f8:2d:f7:38 arp 1
```

lspci (cut down to RT61):
```
02:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```

lshw -C network:
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 78
       serial: 00:04:75:a1:0f:dc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=32 maxlatency=10 mingnt=10 multicast=yes
       resources: ioport:bc00-bc7f iomemory:feafff80-feafffff irq:21
  *-network:1 UNCLAIMED
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:feaf0000-feaf7fff irq:10
  *-network:2
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@02:06.0
       logical name: eth1
       version: 10
       serial: 00:0c:76:97:f2:df
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:b400-b4ff iomemory:feaffe00-feaffeff irq:20
```

cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:04:75:A1:0F:DC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xaf80 

eth1      Link encap:Ethernet  HWaddr 00:0C:76:97:F2:DF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xe00 

eth0:avah Link encap:Ethernet  HWaddr 00:04:75:A1:0F:DC  
          inet addr:169.254.7.90  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xaf80 

eth1:avah Link encap:Ethernet  HWaddr 00:0C:76:97:F2:DF  
          inet addr:169.254.10.225  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xe00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41120 (40.1 KiB)  TX bytes:41120 (40.1 KiB)
```
          
          
          
          
iwconfig:
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by bmeyer on 2007-07-26
*bump*

Also, forgot to mention the card is working perfectly under Windows, so it's not a hardware issue...

---

### Post by bmeyer on 2007-07-27
*bump*
Please, if anyone has any insight to this, I'd greatly appreciate it.  I'm pretty dead in the water...
Thanks in advance!

---

### Post by bmeyer on 2007-07-27
SOLVED
Not sure why this worked, but I tried modprobe ndiswrapper and it suddenly is up and running again.  It's odd since I ndiswrapper -m had already been run.  Oh well...

---

