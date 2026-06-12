---
title: "HP dv3 1075 wireless help"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by XdothedewX on 2011-06-15
So I normally don't ask questions in forums but I have no where else to turn.... I recently installed ubuntu on my HP Pavillion dv3 1075 notebook and I'm pretty excited about using it, however I can't get wireless internet to work.  I have installed the proper driver via NDISWrapper however, to  turn wireless on on my laptop you have to physically push the touch button on the Quick Launch pad, which would be fine but this isn't working.  I don't know if the driver for the Quick Launch pad will work on ubuntu or what.  If someone has a command or something I can do to physically turn my wireless card on, or some solution, I would be eternally grateful. Thank you.

---

### Post by wildmanne39 on 2011-06-15
> **XdothedewX said:**
> So I normally don't ask questions in forums but I have no where else to turn.... I recently installed ubuntu on my HP Pavillion dv3 1075 notebook and I'm pretty excited about using it, however I can't get wireless internet to work.  I have installed the proper driver via NDISWrapper however, to  turn wireless on on my laptop you have to physically push the touch button on the Quick Launch pad, which would be fine but this isn't working.  I don't know if the driver for the Quick Launch pad will work on ubuntu or what.  If someone has a command or something I can do to physically turn my wireless card on, or some solution, I would be eternally grateful. Thank you.
Hi, it is most likely your driver is not installed correctly. Run this command in a terminal so we can see what wireless card you have.
```
lspci
```

---

### Post by XdothedewX on 2011-06-15
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller

00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller

00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)

00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


On my Wireless Network Drivers/Windows Drivers it says bcmwl6 driver is installed and hardware is present.

---

### Post by XdothedewX on 2011-06-15
Any tips?

---

### Post by wildmanne39 on 2011-06-15
> **XdothedewX said:**
> Any tips?
Hi, follow this guide and you should get it working, I believe I remember that you tried to use ndiswrapper, if so remove it first.
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

