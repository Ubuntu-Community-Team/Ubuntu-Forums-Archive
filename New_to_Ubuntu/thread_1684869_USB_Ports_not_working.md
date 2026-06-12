---
title: "USB Ports not working"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by p0ptartz on 2011-02-09
I recently installed Ubuntu 10.10 64-bit and everything worked perfectly (wireless, networking, etc..) or so I thought. For some reason I can't figure out why the USB ports do not work. I'm trying to use my USB mouse and get some files off a USB stick. I have a Dell Inspiron 1546 (laptop) with 3 USB ports. 

I have searched this forum a bunch of times along with Google and can't figure out why they don't work. I have checked my BIOS setting and USB is enabled, and they are up to date. 

In the Terminal I tried typing *lsusb* but nothing happens.
Here's what it says when I type *lspci*
```
ryan@Ryan:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

Appreciate it if anyone could help me out. =]

---

### Post by p0ptartz on 2011-02-10
Anyone? :\

---

### Post by Mark Phelps on 2011-02-10
Some BIOS have "legacy USB" settings. If yours done, try toggling that setting ON and then OFF -- to see if it makes any difference.

---

### Post by p0ptartz on 2011-02-10
Thank you for the help so far. :)

I've tried enabling Legacy USB support and disabling it, along with the actual USB Port settings in the BIOS. Didn't work.

I've checked the Synaptic's Package Manager and installed everything USB related (usbutils and a few other things I saw help some people with the same problem) and still no luck.

Right now I'm try burning 10.04 32-bit to a LiveCD and see if it works.

---

### Post by p0ptartz on 2011-02-10
So I installed Ubuntu 10.04 32-bit.

Everything works perfectly right after install (just had to download the wireless and graphics card drivers).

I wonder why 10.04 works better than the recently released version 10.10? Shouldn't 10.10 be the same thing, with just updated softwares and such? Confuses me.. but oh well. 

tl;dr - Ubuntu 10.04 > 10.10

---

