---
title: "Ethernet does not work, but wifi does"
date: 2016-01-06
forum: Networking &amp; Wireless
---

### Post by myelemes on 2016-01-06
Hello,

OS: [COLOR=#000000]Ubuntu 14.04 LTS

My ehternet does not work, but wifi does. Ethernet worked before, but then it stopped after a while. 
I do not know why it stopped, I can't pinpoint the exact moment when this happened. 

Some commands I ran iin the terminal for troubleshooting:

**~$ sudo ifconfig**

[/COLOR]eth0      Link encap:Ethernet  HWaddr f8:a9:63:4f:b6:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:52 Base address:0xc000 


eth1      Link encap:Ethernet  HWaddr 00:e0:4c:68:01:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:35746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18177278 (18.1 MB)  TX bytes:18177278 (18.1 MB)


wlan0     Link encap:Ethernet  HWaddr 30:3a:64:96:cf:cb  
          inet addr:146.95.217.81  Bcast:146.95.219.255  Mask:255.255.252.0
          inet6 addr: fe80::323a:64ff:fe96:cfcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2267376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4157254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:227023699 (227.0 MB)  TX bytes:5968731386 (5.9 GB)

[B]~$ lspci

[/B]00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5249 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
04:00.0 Network controller: Intel Corporation Wireless 3160 (rev 93)
05:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M] (rev ff)

[B]~$ sudo ifup eth0

[/B]Ignoring unknown interface eth0=eth0.

[B]~$ cat /etc/network/interfaces

[/B]
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback





[B]dmesg | grep -e eth0 -e bcm

[/B]
[   16.849916] eth0: 0xffffc90000cdc000, f8:a9:63:4f:b6:5f, IRQ 52
[   16.902474] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

[B]sudo lshw -C Network

[/B]
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: f8:a9:63:4f:b6:5f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.041.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:52 ioport:4000(size=256) memory:c0604000-c0604fff memory:c0600000-c0603fff
  *-network
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 93
       serial: 30:3a:64:96:cf:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-43-generic firmware=25.17.12.0 ip=146.95.217.81 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:53 memory:c0500000-c0501fff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: eth1
       serial: 00:e0:4c:68:01:0f
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.07.0 (2014/10/09) duplex=full link=no multicast=yes port=MII speed=1Gbit/s

[B]lspci -nn

[/B]
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4)
00:1c.1 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 2 [8086:9c12] (rev e4)
00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
00:1c.4 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 5 [8086:9c18] (rev e4)
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5249] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
04:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
05:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M] [1002:6820] (rev ff)






Please help, my work depends on good ethernet connection.

Thanks,

Mark

---

### Post by myelemes on 2016-01-09
Can somebody please help a guy out here?

Bump*

---

### Post by cariboo on 2016-01-10
I see you marked this thread as solved, can you tell us what you did, so others may benefit from your experience.

---

