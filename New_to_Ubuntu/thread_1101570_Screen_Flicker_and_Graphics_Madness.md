---
title: "Screen Flicker and Graphics Madness"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by conryf on 2009-03-20
I set up Intrepid three days ago and had some minor trouble bootin to my monitor, in particular I had to use sudo poweroff to shutdown. But nothing to complain about.

This morning however I booted up and the monitor was periodically changing color blue black red etc. I rebooted and got the same thing (I was able to login cause my laptop screen was showing the login, after which it went blank). Then it got REALLY wierd. After unplugging my monitor I sucessfully logged in to my laptop, which was dark and my desktop had icons I had never put there, particularly in gnome-panel, also the screen resolution manager (under system->preferences->screen resolution) wasn't able to change anything. Again, I rebooted, this time back to my desktop.

But there was still lots of flickering and just odd behaviour, not responding to keys, responding in the wrong way, opening windows out of the screen view. I have an intel graphics card on a lenovo X61 (see below) and, after surfing the forums with a flickering screen I found someone who said just search synaptic for intel graphics and install anything that looks reasonable, which I did and rebooted again. Now the flickering is still there as are occaisional screen scrambling (notable when [alt]+[tab]ing ) and many reboots later I'm worried about the health of my computer. 

Please help me, I was running hardy with no trouble for about 9 months before a clean install just last week. Thanks!

I am positing the output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)

---

