---
title: "Changing a NIC"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by SteveNorman on 2008-06-28
I am trying to replace my ancient NIC (wired) card with an intel PRO1000 gt desktop adapter. Both are pci.

I cant get online after reboot.
During Boot it goes directly into the intel boot agent and hangs for a bit with this:

DHCP......./

Then it goes into grub. I cant get online in ubuntu or in my XP dual boot.

I cant find anything in bios that indicates that it is booting the intel boot agent first,but it obviously is since it goes there pre-grub. I assumed I would just get right online,,but I am wrong. What are the step required to get online with the new card?

ifconfig with the intel card in gives:
```
eth1      Link encap:Ethernet  HWaddr 00:19:21:28:a6:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdead 

eth2      Link encap:Ethernet  HWaddr 00:1b:21:1c:e0:f7  
          inet6 addr: fe80::21b:21ff:fe1c:e0f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:233864 (228.3 KB)  TX bytes:10071 (9.8 KB)
          Base address:0xbc00 Memory:f9fc0000-f9fe0000 

eth2:avahi Link encap:Ethernet  HWaddr 00:1b:21:1c:e0:f7  
          inet addr:169.254.9.5  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Base address:0xbc00 Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55035 (53.7 KB)  TX bytes:55035 (53.7 KB)

```

lscpi with the card in gives:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:09.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
```

---

### Post by SteveNorman on 2008-06-29
bump

---

