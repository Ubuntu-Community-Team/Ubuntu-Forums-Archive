---
title: "Sound problem"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by markmai86 on 2009-07-27
Hello,

I have just installed the latest version of Ubuntu and I'm pretty new to this.  I have partitionned my hard drive so I can have some programs I still need in windows.

The problem is that my sound works perfectly with windows and I have only a modem sound like with ubuntu (only beeps...)

I have tried some command lines I found on the net but nothing worked.  Maybe the sound is set to a settings which prevents other sounds that beeps, but I can't solve the problem.

I have tried all the options and autodetect in the sound settings preferences (in the system menu) and nothing worked after testing (where I suppose I should here any kind of sound).

So basically when I receive mail with Evolution I get a beep and that is about the only sound I have.

Thanks for helping me

PS:  I have a laptop HP pavillion tx 2000 from 2008

---

### Post by philcamlin on 2009-07-27
please  post the output of "lspci"  :popcorn:

---

### Post by markmai86 on 2009-07-28
the output of lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by Troll_the_Great on 2009-07-28
Try this guide, it helped me allot.
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
Cheers!

---

### Post by markmai86 on 2009-07-28
I have tried your guide.  But even doing exactly what they say in the terminal, I can't get the sound to work.

Does this guide apply to ubuntu as well as it was not explicit (maybe I missed it)?

Thank you

---

