---
title: "Lenovo Y700 Laptop keeps disconnecting wifi"
date: 2016-11-13
forum: Networking &amp; Wireless
---

### Post by exthewifi on 2016-11-13
Hello, I've just recently installed Ubuntu 16.04 after Windows has been causing errors with my laptops GPU. 

I ended up having to go through the rfkill list to enable my wifi card and I was able to connect to my WiFi. However after 10 minutes I would drop WiFi. The only way to get it back would be to restart. 

Attached is the WiFi info txt file that [ATTACH]272116[/ATTACH]

Other info that may help for trouble shooting:
[rfkill list]
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

[lspci]

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1576
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Carrizo (rev c4)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157b
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 157c
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 157c
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157b
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 157c
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1578
00:09.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157d
00:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Device 157a
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 20)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 49)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 49)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 4a)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1570
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1571
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1572
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1573
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1574
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1575
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter
03:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XT [Radeon R9 M280X] (rev ff)

```

---

