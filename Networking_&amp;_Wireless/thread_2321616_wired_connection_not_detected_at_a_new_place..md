---
title: "wired connection not detected at a new place."
date: 2016-04-23
forum: Networking &amp; Wireless
---

### Post by pavan6 on 2016-04-23
Hi..i have just moved to a new place and not able to connect to internet using ethernet cable.

ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 74:86:7a:24:26:4a  
          inet6 addr: fe80::7686:7aff:fe24:264a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:174974184 errors:0 dropped:48 overruns:0 frame:0
          TX packets:58763339 errors:0 dropped:64710 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:220850576128 (220.8 GB)  TX bytes:7785145954 (7.7 GB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:652549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:652549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86763164 (86.7 MB)  TX bytes:86763164 (86.7 MB)


wlan0     Link encap:Ethernet  HWaddr 64:5a:04:53:95:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16626401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7251254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:699785798 (699.7 MB)  TX bytes:1442246980 (1.4 GB)

The RX and TX transfer for ethernet might be of old connection.

output for 
lspci -nn :

00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] [1002:6840] (rev ff)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
08:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)


Help appreciated.

 Thanks

---

### Post by jeremy31 on 2016-04-23
Moved to Networking

---

