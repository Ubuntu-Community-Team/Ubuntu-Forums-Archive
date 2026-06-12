---
title: "graphic issues 64-bit 10.10 ati gfx"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by adobrakic on 2010-11-04
I'm having some graphical issues on my 64-bit Ubuntu 10.10. I have an ATI graphics card. First, and less annoying of the issues, when I autoscroll in firefox (clicking the middle mouse button), FF locks up until the page either scrolls all the way up or all the way down. Obviously, the longer the page, the more annoying... but either way, I don't think scrolling takes up so much memory that FF should freeze completely until it stops scrolling.

Second, all of my full-screen videos are choppy. I figured my card would be enough to play the videos smoothly, so I'm not sure what's going on. Is this a hardware issue, or a Ubuntu issue?

lspci:
```
ado@Ado-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [Non-RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
ado@Ado-PC:~$ 

```

glxgear:
```
ado@Ado-PC:~$ glxgears
8586 frames in 5.0 seconds = 1717.124 FPS
9345 frames in 5.0 seconds = 1868.907 FPS
9286 frames in 5.0 seconds = 1857.032 FPS
9321 frames in 5.0 seconds = 1862.509 FPS
9262 frames in 5.0 seconds = 1852.357 FPS
7367 frames in 5.0 seconds = 1473.374 FPS
8946 frames in 5.0 seconds = 1789.200 FPS
9566 frames in 5.0 seconds = 1913.073 FPS
9359 frames in 5.0 seconds = 1871.723 FPS
7933 frames in 5.0 seconds = 1585.948 FPS
ado@Ado-PC:~$ 

```

---

### Post by coffeecat on 2010-11-05
You have a Radeon HD4200 card. I'm guessing that you installed the proprietary fglrx driver. If so, you would be far better off with the open source driver. I have the Mobility Radeon HD4200 on one of my laptops and I get none of the issues you describe with the open source driver. I get 3d acceleration sufficient for compiz desktop effects and video playback is just fine.

Post back if you need help with reverting to the OS driver.

**Edit:** My comments were based on previous experience of the fglrx driver with the HD4200. I've just tried installing the proprietary driver using the Additional Drivers utility and everything seems fine. I'm not getting the issues you are experiencing - apart from a messed-up Plymouth boot splash, but that is a known problem. So - which driver are you using, and if the proprietary one did you install it with Additional Drivers or download it from the AMD site?

---

### Post by adobrakic on 2010-11-05
I'm at school currently, so I won't be able to test any suggestions, but I installed the driver via Additional Drivers.

---

### Post by adobrakic on 2010-11-06
bump! anyone?

--edit--
i installed the 64-bit flash plugin, and videos aren't choppy anymore. the autoscrolling problem still remains, though.

---

### Post by cejack on 2010-11-07
Here's my setup:

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

My integrated motherboard / video card is completely useless for Compiz and any type of extra or custom desktop effects.  

I've tried everything on the following wiki:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

No dice there...  I've seen some people comment how they're running Compiz with this built-in embedded video.  Would like to know the secret.  (Radeon HD 4200 aka ATI RS880.)

---

### Post by adobrakic on 2010-11-07
that's what I have:

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]

```

and compiz works just fine for me.

---

