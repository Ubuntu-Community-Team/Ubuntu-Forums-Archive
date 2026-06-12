---
title: "Slow Wired Download Speeds"
date: 2016-09-08
forum: Networking &amp; Wireless
---

### Post by davidb82 on 2016-09-08
I'm running Ubuntu 16.04 and am having a weird issue.  I'm hoping someone can help.  When I run an internet speed test I get about 0.5 Mbps download and 4.5 Mbps upload speed.  I'm using a wired connection to my DSL modem. I have another computer running Ubuntu 16.04 that next to this one that is getting about 24 Mbps download and 4.5 Mbps upload speed.  I ran the speed test several times and get similar results.   I swapped network cables and still had the slow speed.  This leads me to believe it is my computer. 

I have a RTL811/8168/8411 PCI Express Gigabit Ethernet Controller according to lshw.  I read some online and saw where the default r8169 driver is problematic.  I followed the advice given to install the r8168-dkms package. It installed fine but did not affect the download speed.   The other computer has the same Ethernet Controller but is still running the default drivers.


Here's some output that is usually requested from what I've seen.  Let me know if any other information would be helpful.

Thanks!

```
 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 02
       serial: 00:24:1d:83:be:e1
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.041.00-NAPI duplex=full ip=192.168.1.66 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:27 ioport:de00(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:fdc00000-fdc0ffff

```

```
david@sparky:~$ ethtool enp2s0
Settings for enp2s0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

```

```
david@sparky:~$ ifconfig -a
enp2s0    Link encap:Ethernet  HWaddr 00:24:1d:83:be:e1  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:302:d1ed:9330:ba0d:327d:2daa:e91b/64 Scope:Global
          inet6 addr: fe80::c54a:f0b4:b596:e99b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50114742 (50.1 MB)  TX bytes:23722014 (23.7 MB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:231214 (231.2 KB)  TX bytes:231214 (231.2 KB)

```


```

david@sparky:~$ dmesg | grep r816
[    1.647205] r8168: module verification failed: signature and/or required key missing - tainting kernel
[    1.647639] r8168 Gigabit Ethernet driver 8.041.00-NAPI loaded
[    1.648492] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    1.648497] r8168  Copyright (C) 2015  Realtek NIC software team <nicfae@realtek.com> 
[    2.098992] r8168 0000:02:00.0 enp2s0: renamed from eth0
[   74.548924] r8168: enp2s0: link up
```

---

### Post by praseodym on 2016-09-09
[http://packages.ubuntu.com/yakkety/r8168-dkms](http://packages.ubuntu.com/yakkety/r8168-dkms)

Try the latest driver, version 42 and/or deactivating IPv6

---

### Post by davidb82 on 2016-09-10
Thanks for the replay. I tried both.  The only change is that my upload speed is now about the same as my download speed.  Checked speeds on the second computer and it remains unchanged.  I'm going to grab another network card and try it.  Perhaps it is a hardware problem.

---

### Post by davidb82 on 2016-09-11
I got a new card installed in my computer.  Ubuntu recognized it without an issue.  Speed test with the new card matched the numbers from the other computer.  Call this one resolved.  Thanks!

---

