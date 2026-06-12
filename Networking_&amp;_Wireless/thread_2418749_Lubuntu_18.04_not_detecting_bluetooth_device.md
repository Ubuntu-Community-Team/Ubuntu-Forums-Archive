---
title: "Lubuntu 18.04 not detecting bluetooth device"
date: 2019-05-10
forum: Networking &amp; Wireless
---

### Post by claretremaine on 2019-05-10
Hi

I really need to transfer some photos from my phone to PC but cannot get bluetooth to work for love nor money.
The computer is detecting bluetooth device....but only up to a point.
lspci -nnk | grep -iA2 net; lsusb; dmesg | egrep -i 'blue|firm'
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Dell Wireless 1506 WLAN Half Mini-Card [1028:0208]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:0576]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0b05:1715 ASUSTek Computer, Inc. 2045 Bluetooth 2.0 Device with trace filter
Bus 001 Device 003: ID 1058:1001 Western Digital Technologies, Inc. Elements Desktop (WDE1U)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:08ce Logitech, Inc. QuickCam Pro 5000
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.028895] Spectre V2 : Enabling Restricted Speculation for firmware calls
[   11.802919] Bluetooth: Core ver 2.22
[   11.802933] Bluetooth: HCI device and connection manager initialized
[   11.802936] Bluetooth: HCI socket layer initialized
[   11.802938] Bluetooth: L2CAP socket layer initialized
[   11.802943] Bluetooth: SCO socket layer initialized
[   18.766776] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.766777] Bluetooth: BNEP filters: protocol multicast
[   18.766780] Bluetooth: BNEP socket layer initialized

































But if when I open blueman it says that there is no device detected !!  This is what I get:
hcitool dev
Devices:

Doesn't appear blocked
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Tried this: [https://www.quora.com/How-do-I-fix-Ubuntu-16-04-Bluetooth-issues](https://www.quora.com/How-do-I-fix-Ubuntu-16-04-Bluetooth-issues), changing AutoEnable to true from false, and various other methods. Now completely stuck! Anyone know what else I can do?

---

