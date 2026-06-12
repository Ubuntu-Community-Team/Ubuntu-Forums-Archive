---
title: "How do I find out what sound driver i need?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by austinpsycho on 2009-07-04
lsusb lists ```
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 056a:0017 Wacom Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```lspci lists ```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by ~sHyLoCk~ on 2009-07-04
Try ```
sudo alsaconf
alsamixer
alsactl store
```

---

### Post by cariboo on 2009-07-04
I would check to see if the drivers are already loaded. In a terminal type:

```
lsmod |grep snd
```

---

### Post by Favux on 2009-07-04
Hi austinpsycho,

And the following in a terminal:
```
aplay -l
```
will tell you what sound card you have.

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
``` ?

---

