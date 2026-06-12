---
title: "Wireless Card Detected but no wlan0"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Stalin828 on 2008-08-17
First of all, I am a linux noob so please be specific.

My wireless card is detected. I can see it in lswh. However I have no wlan0. When I first installed Hardy Heron my wireless was detected as wlan0, but I could not connect to my WEP network. So, I installed ndiswrapper and it worked fine. I recently uninstalled ndiswrapper to try b43-fwcutter to see if I could get it to work. However, now I have no wlan0. I can reinstall ndiswrapper and then my wireless works fine again.

lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 20
       serial: 00:0b:cd:15:25:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=198.18.101.188 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=0

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0b:cd:15:25:82  
          inet addr:198.18.101.188  Bcast:198.18.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20b:cdff:fe15:2582/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000 
          RX bytes:1459119 (1.3 MB)  TX bytes:282670 (276.0 KB)
          Interrupt:11 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70300 (68.6 KB)  TX bytes:70300 (68.6 KB)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

Thanks for any help!

---

### Post by Stalin828 on 2008-08-17
Managed to solve it on my own. There were some old ndiswrapper config files floating around. After removing them my wireless started working perfectly again.

---

### Post by Crafty Kisses on 2008-08-17
Nice, mark the thread as solved. :)

---

