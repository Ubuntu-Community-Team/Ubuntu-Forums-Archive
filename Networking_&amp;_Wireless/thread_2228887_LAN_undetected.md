---
title: "LAN undetected"
date: 2014-06-10
forum: Networking &amp; Wireless
---

### Post by harshatts on 2014-06-10
I have Ubuntu 12.10. wireless works perfectly fine. one particular LAN connection works one, while the other LAN in the same university campus with the same proxy settings does not work. in windows partition both wireless and lan work. When i remove and replug the lan cable the Ubuntu network settings detects for a moment and then says unplugged. in the virtual box windows xp it detects lan connection but does not connect to internet. the ethernet modem is fine when checked with if config and lspci. it is not a hardware issue, some kind of a setting issue. could somebody help!!

here are ifconfig and lspci run details

ifconfig

eth0      Link encap:Ethernet  HWaddr 10:bf:48:08:7a:09  
          inet6 addr: fe80::12bf:48ff:fe08:7a09/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2588 (2.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2244 (2.2 KB)  TX bytes:2244 (2.2 KB)

wlan0     Link encap:Ethernet  HWaddr 94:db:c9:9a:23:c4  
          inet addr:192.168.11.176  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::96db:c9ff:fe9a:23c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7234745 (7.2 MB)  TX bytes:1698342 (1.6 MB)



lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 630M] (rev ff)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

### Post by praseodym on 2014-06-10
Hi,

12.10 was running out some weeks ago. I recommend installing 14.04 LTS.

---

### Post by harshatts on 2014-06-11
thanks for the suggestion. it seems to work with other lan points, so not ubuntu i guess but still curious..

---

