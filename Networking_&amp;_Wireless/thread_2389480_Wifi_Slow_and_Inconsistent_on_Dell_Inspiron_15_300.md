---
title: "Wifi Slow and Inconsistent on Dell Inspiron 15 3000 Series"
date: 2018-04-17
forum: Networking &amp; Wireless
---

### Post by beanyak on 2018-04-17
```

alex@bbq:~$ lspci00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1576
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 1577
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 98e4 (rev c0)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15b3
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157b
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 157c
00:02.5 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 157c
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157b
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1578
00:09.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157d
00:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Device 157a
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 20)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 4b)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 49)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 4b)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15b5
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
[B]16:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
[/B]
```

I'm dual booting Windows and Ubuntu on Dell Inspiron 15 3000 Series. I've been running Ubuntu for the most part, and the wifi is decent at times, but I waste a lot of time waiting for the wifi. On windows, I speedtested (although only once) and got 20Mb/s down, and something similar up. On Ubuntu, I've gotten about .5Mb/s down and something similar up.

What I've tried:
- [https://askubuntu.com/questions/887238/atheros-qca9565-ar9565-unstable-connection-slow-wireless-ubuntu-16-04](https://askubuntu.com/questions/887238/atheros-qca9565-ar9565-unstable-connection-slow-wireless-ubuntu-16-04)
- Disabling IPv6 support: 
  - manually for the two wifi connections I try, and, 
  - within some config file ([https://askubuntu.com/a/790022](https://askubuntu.com/a/790022))
- one fix that suggested adding a country code to some file
- [https://askubuntu.com/a/470171](https://askubuntu.com/a/470171) - couldn't proceed because, running make, I got "[COLOR=#111111][FONT=Ubuntu]ERROR: compat-drivers by default supports kernels >= 2.6.24, try enabling only one driver though"
and maybe a thing or two more.[/FONT][/COLOR]

---

