---
title: "Wifi doesn't work (no wlan0 after installation)"
date: 2015-06-19
forum: Networking &amp; Wireless
---

### Post by dowoshek on 2015-06-19
Hello,
Network Manager shows no wireless options. It's old Asus laptop, eth0 works without problems. Before installing Lubuntu 14.04 I tried to install Xubuntu 14.04 twice and the installation stopped and was hanging at the same point: "configuring bcmwl-kernel-source". The Lubuntu installation was without problems and I see the package installed. I've already installed firmware-b43-installer but it doesn't help.
Please, ask for any files/commands you'd like to see.

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:b4:2e:30  
          inet6 addr: fe80::218:f3ff:feb4:2e30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3482416 (3.4 MB)  TX bytes:468223 (468.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116907 (116.9 KB)  TX bytes:116907 (116.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:78.10.54.233  P-t-P:83.238.252.33  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1156415 (1.1 MB)  TX bytes:124617 (124.6 KB)
```

lspci
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC410 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RC410M [Mobility Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

---

### Post by wildmanne39 on 2015-06-19
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by dowoshek on 2015-06-19
I've just solve it myself. Just remove bcmwl-kernel-source and THEN install firmware-b43-installer :)

---

### Post by wildmanne39 on 2015-06-19
Please use thread tools to mark the thread solved!
Thanks

---

