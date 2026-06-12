---
title: "ATI Maverick White/Black Screen of Death"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by teamcoltra on 2010-10-22
I am having an issue that it seems others are having, but my issue is a bit different. My computer just randomly gives me a white screen, or a black screen, and sometimes lines of both... and is unresponsive, I have to physically hold the power button to turn off my computer.

I am on the computer now, it doesn't happen on boot or anything, it just happens randomly. 


lspci:
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by teamcoltra on 2010-10-22
In the last Ubuntu (The L one... lovely linx or lonely lemer or whatever), when I used the ATI graphics driver, my graphics were really screwed up, so I used the kernel one... which worked great.

---

### Post by aofc on 2010-10-31
Ok, sorry for crossposting, but I think this might be a more appropriate place. 

I have the same problem, while I have been using 10.10 for about two months now (started with the release candidate, from upgrade), it was working fine until a few days ago when this started to happen. Maybe an update is causing the problem?

Also, I just switched to the beta Flash 64bit driver (which works great), and this problem started early after that, although I don't think they're related since I think this happened when I was not using any flash.

Ubuntu 10.10 64bit with latest updates (from Proposed rep)
CPU : Intel Core2 Duo T6600 2.20GHz
Memory : 4Gb
Video : Mobility Radeon HD 3400 series (with open source drivers)

And actually the system seems to be still running, only the video crashes, with a white screen or a what seems to be purple vertical lines on a white background. Keyboard is still responding (at least Caps lock) and music keeps playing. I can't seem to be able to switch to another session with Ctrl-Alt-F# though.

This happens every couple of hours.

---

### Post by teamcoltra on 2010-11-08
Yes, this exactly... if it happens while I am using the computer, my system freezes up for a second, but then the screen goes white but with these vertical lines....

It can also happen though when my screen is off (after my system has been idol for hours), in this case the screen stays black.

---

