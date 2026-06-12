---
title: "[SOLVED] Having trouble even enabling Broadcom card."
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by yatesl on 2008-06-01
I'm on a Dell Inspiron 6400, with a Broadcom wireless card.  My wireless internet connection isn't working, and after browsing the forums/looking about in Terminal, I've found the problem:

```
liam@liam-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:01:a6:e7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5b:d5:1c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
```

As you can see, the card isn't even enabled.  The hotkey to enable/disable it is Fn+F2.  However, when I press that in Ubuntu, nothing happens.  The light doesn't go off (if it's on originally), or come on.

Not sure if this is useful, but

```
liam@liam-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:5B:D5:1C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19312 (18.8 KB)  TX bytes:19312 (18.8 KB)
```


Thanks in advance if anyone can help.



Update: Disregard this, problem solved.  I just hooked it up to the Internet via ethernet, and downloaded the restricted driver.

---

