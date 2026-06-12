---
title: "[SOLVED] Thinkpad T61 wireless won't connect"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by thetejon on 2008-07-27
I have a Thinkpad T61 running 8.04.  I have an Atheros AR5212 wireless card that suddenly stopped connecting to my wireless router about 2 weeks ago.  I've seen some people having problems with the latest kernel and wireless, but I'm using the 2.6.24-19-generic kernel, and I think that one's okay.  The router is a Linksys WRT54GP2.

I know the wireless works, because I can connect to my neighbor's network.  And I know my router works, because my work laptop (Windows XP) and my wife's laptop (OSX) connect without a problem.

How do I diagnose the problem?

---

### Post by thetejon on 2008-07-28
lspci
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
```

ifconfig
```
ath0      Link encap:Ethernet  HWaddr 00:1c:26:40:af:f3  
          inet6 addr: fe80::21c:26ff:fe40:aff3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1c:25:10:1d:bf  
          inet addr:192.168.15.102  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe10:1dbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:18295376 (17.4 MB)  TX bytes:1496767 (1.4 MB)
          Base address:0x1840 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96300 (94.0 KB)  TX bytes:96300 (94.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1C-26-40-AF-F3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8534 errors:0 dropped:0 overruns:0 frame:1971
          TX packets:199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:815881 (796.7 KB)  TX bytes:9154 (8.9 KB)
          Interrupt:17 
```

iwconfig
```

ath0      Link encap:Ethernet  HWaddr 00:1c:26:40:af:f3  
          inet6 addr: fe80::21c:26ff:fe40:aff3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1c:25:10:1d:bf  
          inet addr:192.168.15.102  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe10:1dbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:18295376 (17.4 MB)  TX bytes:1496767 (1.4 MB)
          Base address:0x1840 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96300 (94.0 KB)  TX bytes:96300 (94.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1C-26-40-AF-F3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8534 errors:0 dropped:0 overruns:0 frame:1971
          TX packets:199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:815881 (796.7 KB)  TX bytes:9154 (8.9 KB)
          Interrupt:17 

```

---

### Post by thetejon on 2008-07-31
Fixed.  All I had to do was delete the entry for my network from the network manager, and it connected right away.  And I feel a little dumb for not trying that a month ago.

---

