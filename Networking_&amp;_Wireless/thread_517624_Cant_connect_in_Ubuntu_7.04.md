---
title: "Cant connect in Ubuntu 7.04"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Maischoyu on 2007-08-04
My computer was connected directly through LAN to my dad's desktop, he uses Prolink 8000 Network type. Yesterday, i tried ubuntu 7.04 installed it from live cd (after i use the old ubuntu 6.06). After i login I cant seem to connect internet at all in ubuntu 7.04 but strangely this is not happened in ubuntu 6.06. Can tell me why i can connect w/o problem in old ubuntu but having trouble in ubuntu 7.04? because now I'm using back to my old ubuntu 6.06 :( thanks..

```
**maischoyu@maischoyu-desktop:~$ lshw -C network**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@02:0c.0
       logical name: eth0
       version: 10
       serial: 00:10:dc:9e:a9:e6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:c000-c0ff iomemory:e6010000-e60100ff irq:19
-------------------------------------------------------------------------
**maischoyu@maischoyu-desktop:~$ ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:10:DC:9E:A9:E6  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103446 (101.0 KiB)  TX bytes:88020 (85.9 KiB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
-------------------------------------------------------------------------
**maischoyu@maischoyu-desktop:~$ sudo ethtool eth0**
Password:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes
-------------------------------------------------------------------------
```

help me please...

**EDIT: PROBLEM SOLVED! :D "IT'S A HOST PROBLEM".**

---

### Post by Maischoyu on 2007-08-04
**solved**

---

### Post by The-Organist on 2007-08-04
What was the HOST problem?

---

