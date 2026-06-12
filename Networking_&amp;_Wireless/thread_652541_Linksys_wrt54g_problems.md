---
title: "Linksys wrt54g problems"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by Homicide on 2007-12-28
Hello everyone. I'm having trouble using my Linksys WRT54G with a wired connection. I'm dual booting XP and Ubuntu and when I boot into Ubuntu, I cannot connect. I have tried pinging my router with no luck.

I had XP set up to use a static IP, but the using the same settings in ubuntu didn't work at all. It's corrently set to DHCP, but Ubuntu doesn't recognize that either.

I tried solutions from every other thread, but nothing worked. I'm sick of having to boot to windows when I want to use the internet.

lspci outputs:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
00:11.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:14.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
01:05.0 VGA compatible controller: Silicon Integrated Systems [SiS] 315PRO PCI/AGP VGA Display Adapter
```

These are my static IP settings

```

Network device:	eth0
Hardware address:	00:50:fc:0d:84:2b
IP address:	192.168.1.100
Netmask:	255.255.255.0
Broadcast:	192.168.1.255
Multicast:	Enabled
MTU:	1500
Link speed:	not available
State:	Active
Transmitted packets:	0
Transmission errors:	0
Received packets:	0
Reception errors:	0
Collisions:	0

-------------------------------------------------------------------------

alan@AIDS:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:FC:0D:84:2B  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0xf00 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

alan@AIDS:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

When I use DHCP, I get this.

```

alan@AIDS:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

Any help is appreciated.

Edit: Nevermind, it was a problem with my ethernet device. I predict this thread will slowly disappear.

---

