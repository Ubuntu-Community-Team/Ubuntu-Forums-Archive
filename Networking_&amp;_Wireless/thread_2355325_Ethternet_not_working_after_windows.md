---
title: "Ethternet not working after windows"
date: 2017-03-11
forum: Networking &amp; Wireless
---

### Post by sawfly on 2017-03-11
I have 2 OS Ubuntu 16.04 and windows. If i run windows and use internet, after reboot to ubuntu it can't connect to internet. I i don't use internet 1 day, I can use internet in ubuntu. May be someone had same problem and solved it. Here some info:
```
ifconfig -a | grep eth
-empty

sudo lshw -class network

*-network    
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 06
       serial: f4:6d:04:d1:b6:1f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.043.02-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:30 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbff8000-fbffbfff

Settings for enp3s0:
    Supported ports: [ TP ]
    Supported link modes:  10baseT/Half 10baseT/Full
                            100baseT/Half 100baseT/Full
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes

    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no

ifconfig
enp3s0    Link encap:Ethernet  HWaddr f4:6d:04:d1:b6:1f
          inet6 addr: fe80::f763:620:9e66:5326/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10380 (10.3 KB)  TX bytes:13275 (13.2 KB)
          Interrupt:30 Base address:0x8000
lo           Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:33497 (33.4 KB)  TX bytes:33497 (33.4 KB)

```

---

### Post by sawfly on 2017-03-15
So. I could not connect to Ethernet automatic. So i got Ip, mask, gateway and dns servers, and set them manual.

---

