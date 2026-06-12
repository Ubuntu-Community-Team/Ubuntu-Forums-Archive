---
title: "Network Unclaimed"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by Celauran on 2010-09-01
My 10.04 install has an onboard NIC as well as a 4-port Adaptec PCI NIC.  The onboard card is working perfectly but the Adaptec card does not come up.

lshw -C network:
```
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: ANA620xx/ANA69011A
       vendor: Adaptec
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=9
       resources: memory:ef000000-ef07ffff ioport:a000(size=256) memory:40000000-4003ffff(prefetchable)
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: ANA620xx/ANA69011A
       vendor: Adaptec
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=9
       resources: memory:ef080000-ef0fffff ioport:a400(size=256) memory:40040000-4007ffff(prefetchable)
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: ANA620xx/ANA69011A
       vendor: Adaptec
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=9
       resources: memory:ef100000-ef17ffff ioport:a800(size=256) memory:40080000-400bffff(prefetchable)
  *-network:3 UNCLAIMED
       description: Ethernet controller
       product: ANA620xx/ANA69011A
       vendor: Adaptec
       physical id: 7
       bus info: pci@0000:02:07.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=9
       resources: memory:ef180000-ef1fffff ioport:ac00(size=256) memory:400c0000-400fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: 8255xER/82551IT Fast Ethernet Controller
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:04:09.0
       logical name: eth0
       version: 09
       serial: boo
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A ip=10.0.0.2 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:17 memory:f4022000-f4022fff ioport:b000(size=64) memory:f4000000-f401ffff memory:40100000-401fffff(prefetchable)
```

lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] System Controller (rev 11)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] AGP Bridge
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-768 [Opus] ISA (rev 05)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-768 [Opus] IDE (rev 04)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-768 [Opus] ACPI (rev 03)
00:07.5 Multimedia audio controller: Advanced Micro Devices [AMD] AMD-768 [Opus] Audio (rev 03)
00:08.0 PCI bridge: Intel Corporation 21154 PCI-to-PCI Bridge
00:09.0 PCI bridge: Adaptec (formerly DPT) PCI Bridge (rev 01)
00:09.1 I2O: Adaptec (formerly DPT) SmartRAID V Controller (rev 01)
00:10.0 PCI bridge: Advanced Micro Devices [AMD] AMD-768 [Opus] PCI (rev 05)
01:05.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
02:04.0 Ethernet controller: Adaptec ANA620xx/ANA69011A (rev 03)
02:05.0 Ethernet controller: Adaptec ANA620xx/ANA69011A (rev 03)
02:06.0 Ethernet controller: Adaptec ANA620xx/ANA69011A (rev 03)
02:07.0 Ethernet controller: Adaptec ANA620xx/ANA69011A (rev 03)
04:00.0 USB Controller: Advanced Micro Devices [AMD] AMD-768 [Opus] USB (rev 07)
04:05.0 USB Controller: NEC Corporation USB (rev 41)
04:05.1 USB Controller: NEC Corporation USB (rev 41)
04:05.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
04:09.0 Ethernet controller: Intel Corporation 8255xER/82551IT Fast Ethernet Controller (rev 09)
```

/etc/udev/rules.d/70-persistent-net.rules:
```
# PCI device 0x8086:0x1209 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="snip", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x9004:0x6915 (starfire)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="snip", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x9004:0x6915 (starfire)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="snip", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x9004:0x6915 (starfire)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="snip", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

# PCI device 0x9004:0x6915 (starfire)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="snip", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"
```

The card is clearly there and recognized, and yet..

ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr blah  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fe4c:eedf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7046 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1049 txqueuelen:1000 
          RX bytes:1221906 (1.2 MB)  TX bytes:2525764 (2.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22563 (22.5 KB)  TX bytes:22563 (22.5 KB)


```

What am I missing here?

---

### Post by theDaveTheRave on 2010-09-02
Celauran

I'm guessing that you are able to get online?

The thing is I also guess you have given the full output of your ```
ifconfig -a
```

I guess that the reason eth0 isn't being claimed is because your cable is plugged into a different port.

if you move it around you will find that you get an IP address at a different interface.

I'm not sure you would be able to loop them to one another though, unless your system is acting as a dhcp also?

David

---

### Post by Celauran on 2010-09-02
Sorry, yes that's the full output of ifconfig.  eth0 is fine, none of the NICs on the 4-port card are.  All five are connected to the same hub.

---

### Post by SlugSlug on 2010-09-02
sudo ifconfig eth1 up



whats that do?

---

### Post by Celauran on 2010-09-02
```

[~]$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

```

---

### Post by SlugSlug on 2010-09-02
I think it may be the driver.. does anything show up in that restricted drivers app?

if not it maybe a case of searching for something like nswrapper -- but thats only a guess

---

### Post by Celauran on 2010-09-02
It uses the starfire driver which, according to lsmod, is loaded fine.  I'm afraid I don't know what 'restricted drivers app' you're referring to.

---

### Post by SlugSlug on 2010-09-02
> **Celauran said:**
> It uses the starfire driver which, according to lsmod, is loaded fine.  I'm afraid I don't know what 'restricted drivers app' you're referring to.


not on my box at mo but i think it's just called 'hardware drivers' in system menu

but if the driver is loaded am out of ideas

---

### Post by Celauran on 2010-09-02
Ah.  This is a server box, so no GUI.

---

### Post by scooby2 on 2010-09-11
I'm having the same problem with Ubuntu 10.04. The Starfire card works fine under Centos 5.x which uses 2.6.18. Tried booting with noapic, irqpoll, etc with no luck. Any ideas?

dmesg shows:

[203284.702856] starfire.c:v1.03 7/26/2000  Written by Donald Becker <becker@scyld.com>
[203284.702859]  (unofficial 2.2/2.4 kernel port, version 2.1, July  6, 2008)
[203284.702862] starfire: polling (NAPI) enabled
[203284.702919] ioremap: invalid physical address fffffffffe500000
[203284.702923] starfire 0: cannot remap 0x80000 @ 0xfe500000, aborting
[203284.703204] ioremap: invalid physical address fffffffffe600000
[203284.703209] starfire 1: cannot remap 0x80000 @ 0xfe600000, aborting
[203284.703428] ioremap: invalid physical address fffffffffe680000
[203284.703432] starfire 2: cannot remap 0x80000 @ 0xfe680000, aborting
[203284.703649] ioremap: invalid physical address fffffffffe780000
[203284.703653] starfire 3: cannot remap 0x80000 @ 0xfe780000, aborting

---

### Post by jbroxon1 on 2011-07-12
Mine was working fine- I have 3 quad cards.  2 are happy meal drivers and 1 is the starfire.  After a recent reboot, I just lost the starfire.  All 4 ports are missing - eth1, 3, 5 and 7. 

root@Ubuntu:/etc/udev/rules.d#  ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:22:63:ee:2a
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:fe63:ee2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:139893 (139.8 KB)  TX bytes:276672 (276.6 KB)
          Interrupt:26 Base address:0xc000

eth2      Link encap:Ethernet  HWaddr 08:00:20:ae:9f:6c
          inet6 addr: fe80::a00:20ff:feae:9f6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:1494 (1.4 KB)
          Interrupt:21 Base address:0x5000

eth4      Link encap:Ethernet  HWaddr 08:00:20:ae:9f:6d
          inet6 addr: fe80::a00:20ff:feae:9f6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
          Interrupt:22 Base address:0x7000

eth6      Link encap:Ethernet  HWaddr 08:00:20:ae:9f:6e
          inet6 addr: fe80::a00:20ff:feae:9f6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:23 Base address:0x1000

eth8      Link encap:Ethernet  HWaddr 08:00:20:ae:9f:6f
          inet6 addr: fe80::a00:20ff:feae:9f6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:1494 (1.4 KB)
          Interrupt:20 Base address:0x3000

eth9      Link encap:Ethernet  HWaddr 08:00:20:a4:19:50
          inet6 addr: fe80::a00:20ff:fea4:1950/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:22 Base address:0x5000

eth10     Link encap:Ethernet  HWaddr 08:00:20:a4:19:51
          inet6 addr: fe80::a00:20ff:fea4:1951/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:1494 (1.4 KB)
          Interrupt:23 Base address:0x7000

eth11     Link encap:Ethernet  HWaddr 08:00:20:a4:19:52
          inet6 addr: fe80::a00:20ff:fea4:1952/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:20 Base address:0x9000

eth12     Link encap:Ethernet  HWaddr 08:00:20:a4:19:53
          inet6 addr: fe80::a00:20ff:fea4:1953/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
          Interrupt:21 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)



What should i do??

---

