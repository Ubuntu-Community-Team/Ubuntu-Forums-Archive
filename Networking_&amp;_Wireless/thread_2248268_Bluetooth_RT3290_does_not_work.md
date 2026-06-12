---
title: "Bluetooth RT3290 does not work"
date: 2014-10-13
forum: Networking &amp; Wireless
---

### Post by JVvm1UA6 on 2014-10-13
Hi!
I have a problem with the bluetooth. I installed Ubuntu 14.04, but it does not recognize my bluetooth device a Ralink RT3290. I looked for a solution in internet, but I have not solved the problem.
I saw that in some way the output of the following commands can be useful.
```
luca@luca-ultrabook:~$ lspci00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] (rev ff)
07:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
07:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
08:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
08:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth

luca@luca-ultrabook:~$ hcitool dev
Devices:
luca@luca-ultrabook:~$ 
```
Do you have any idea?

---

### Post by jeremy31 on 2014-10-14
Look at comment 80 and after, looks like limited success
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721)

---

