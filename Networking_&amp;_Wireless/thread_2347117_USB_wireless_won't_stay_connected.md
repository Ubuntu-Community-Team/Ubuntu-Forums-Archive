---
title: "USB wireless won't stay connected"
date: 2016-12-21
forum: Networking &amp; Wireless
---

### Post by hyburn on 2016-12-21
I recently installed 16.04 with a wireless card that was not supported at all (AE2500). so I pulled out an old TP link TL-WN821N, and it works, but this device is not staying connected for very long

```
lspci:
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)


lsusb:
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 006: ID 0cf3:9170 Atheros Communications, Inc. AR9170 802.11n     <--------------------------------------thats the wireless USB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

suggestions?

---

### Post by wildmanne39 on 2016-12-21
Please post the info from the wireless script in my signature.
Edited

---

### Post by jeremy31 on 2016-12-21
And it wouldn't hurt to see our friend chili555's standard words of wisdom concerning wifi on Linux [http://askubuntu.com/a/862815/300665](http://askubuntu.com/a/862815/300665)

---

