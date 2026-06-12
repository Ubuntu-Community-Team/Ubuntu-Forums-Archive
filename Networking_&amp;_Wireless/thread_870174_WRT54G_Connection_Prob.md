---
title: "WRT54G Connection Prob"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by ptty97 on 2008-07-25
I have a old HP Pavilion ZV5000 with a corrupt windows that is unusable. I have tried the U8.4 from the disk and it loaded fine with one exception. My wireless connection does not work. I have a WRT54G and it will not connect. With my corrupt windows I can not access the INF file to allow it to use a windows driver. Any help here?
This is my first experience with Linux so pls bear with my obviously simple questions and pls provide any help in neophyte terms. Tks much in advance.

---

### Post by PinkFloyd102489 on 2008-07-25
Open a terminal, input these commands, and post the output here.


```
lspci
```
```
lshw -C Network
```

---

### Post by ptty97 on 2008-07-27
[SIZE="2"]> **PinkFloyd102489 said:**
> Open a terminal, input these commands, and post the output here.


```
lspci
```
```
lshw -C Network
```

lspci

00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)


lshw -C Network
      
  *-network DISABLED
       description: Wireless interface
       physical id: 1
      serial: 00:90:4b:91:22:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

[/SIZE]

by reading the above, i'm guessing i need to enable the network. I went to the network icon and it show the enable network is checked but when opening there is no network identified. Thanks in advance for the assist.....ptty97

---

