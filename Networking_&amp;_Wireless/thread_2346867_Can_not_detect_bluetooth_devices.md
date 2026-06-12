---
title: "Can not detect bluetooth devices"
date: 2016-12-19
forum: Networking &amp; Wireless
---

### Post by maherson on 2016-12-19
Dears

Am new at linux and i have Ubuntu 16.4.1 LTS. Everything is great but ,i cant detect any bluetooth devices ,even when i try to add any device ,it keep searching for long time with no result .

I ran two commands and here its results

[B][SIZE=3]lspci [/SIZE]
[/B]
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 05)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

and [SIZE=3][B][COLOR=#111111][FONT=Consolas]lspci -knn | grep Net -A2; lsusb
[/FONT][/COLOR][/B][/SIZE]
01:00.0 Network controller [0280]: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip] [1814:539f]
    DeviceName: Ralink WLAN Ralink Rashi2 RT5390BC8_802.11 b/g/n 1x1 PCIe HMC
    Subsystem: Hewlett-Packard Company RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip] [103c:1774]
Bus 002 Device 003: ID 090c:237c Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 148f:2000 Ralink Technology, Corp. 
Bus 001 Device 003: ID 1d57:fa60 Xenta 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 248a:8566  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

can you help me to be able to detect bluetooth devices 

thanks

---

