---
title: "Ethernet card not working correctly."
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by Private_Ops on 2008-12-02
I've got a Compaq V6500z laptop running [Crunchbang]("http://crunchbang.org/") Linux (current release based on ubuntu 8.10).


Everything is great, even the wireless with the closed source driver.
Problem is the onboard ethernet does not work. I can get an IP using "ifup eth0". I even got it to install iptraf through command line. That's it though. I can't get internet (as far as web pages and stuff goes (I can't even ping)).

lspci output

> 
ops@ops-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
ops@ops-laptop:~$ 




ifconfig output

> 
ops@ops-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:ca:f7:56  
          inet addr:192.168.130.159  Bcast:192.168.143.255  Mask:255.255.240.0
          inet6 addr: fe80::21b:24ff:feca:f756/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9102 errors:6 dropped:0 overruns:0 frame:6
          TX packets:362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:851041 (851.0 KB)  TX bytes:93229 (93.2 KB)
          Interrupt:220 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:de:ff:cb  
          inet6 addr: fe80::21a:73ff:fede:ffcb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:54
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1300 (1.3 KB)  TX bytes:1300 (1.3 KB)

ops@ops-laptop:~$ 


Note: eth1 is my wireless.

---

### Post by Iowan on 2008-12-02
Post contents of */etc/network/interfaces*.  How does machine get address - static, DHCP? Non-standard netmask (and broadcast address) aren't necessarily wrong - unless router/gateway is unreachable.

---

### Post by Private_Ops on 2008-12-02
/etc/network/interfaces

> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


---

### Post by Iowan on 2008-12-02
Next question - what is supplying the DHCP address - modem, router, a local DHCP server?

---

### Post by Private_Ops on 2008-12-02
> **Iowan said:**
> Next question - what is supplying the DHCP address - modem, router, a local DHCP server?

Here at school it's a local DHCP server. At home my firewall supplies it for wired connections and my router does it for wireless (can't fully operate as an AP).

---

