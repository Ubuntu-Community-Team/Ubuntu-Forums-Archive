---
title: "Not able to receive IP via DHCP; nVidia MCP51 in Edgy"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by Okiesmokie on 2007-01-27
I've been stumbling across this problem for the past few days, and honestly I have no clue how I can fix it.  It has happened in every linux distribution I've tried (Fedora Core 5, Fedora Core 6, SuSE 10.2, Ubuntu Dapper and Ubuntu Edgy) and I have been advised to attempt to solve this problem in Ubuntu Edgy; and when I do, I intend to continue to use Ubuntu.

The problem is that DHCP is not assigning my computer an IP address.

I am using a standard Cable Connection, but am not going through a router and am not hooked up to a LAN.  All of the computers in my house are running through a hub and have their own separate IP addresses.

Here is the output to some of the files that may give you insight as to how to assist me in solving this problem.

**# lspci**
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
**00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)**
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
04:0a.0 Communication controller: Agere Systems Unknown device 0620
```


**# dmesg | eth0**
```
[17179577.348000] eth0: forcedeth.c: subsystem: 0103c:2a3a bound to 0000:00:14.0
[17179616.376000] eth0: no IPv6 routers present
```


**# route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```


**# ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:17:31:24:60:CC  
          inet6 addr: fe80::217:31ff:fe24:60cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1227468 (1.1 MiB)  TX bytes:15516 (15.1 KiB)
          Interrupt:225 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14976 (14.6 KiB)  TX bytes:14976 (14.6 KiB)
```


I would be extremely greatful if someone could lend me a hand in solving this issue.  If there is any more info you need, just ask and I will do my best to retrieve it.

---

### Post by Okiesmokie on 2007-01-27
bump

---

### Post by swaroopch on 2007-03-05
Hi,

I'm facing the same problem. Did you find a solution?

Thanks!

---

