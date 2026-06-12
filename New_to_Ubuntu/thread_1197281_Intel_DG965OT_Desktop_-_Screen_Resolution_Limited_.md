---
title: "Intel DG965OT Desktop - Screen Resolution Limited to 1360x768"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by imwithid on 2009-06-25
I run a dual boot system (Windows XP-x64 and Jaunty 64-bit). Under the XP driver, I am able to attain a 1920x1200 (WUXGA)resolution (up to a maximum of 2560x1600 - WQXGA - limited to 1920x1200 by my monitor - an ACER AL2216W). I don't think that this is limited to Jaunty as I have tried the live version of 8.04.2 and 8.10 (I think the resolution is limited to 1024x768 until I tinker with fixing this to reach the upper limit without having a portion of the right side of the screen cut off).

I have yet to achieve anything beyond 1360x768.Also, the brightness of the screen is intense (I'm light sensitive). I can adjust the dimming level through the XP driver, however, I have tried using the dimming application and it never works (presumably because it cannot detect the monitor and thus it's hardware?).

My system vitals are as follows:

        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82G965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0

lspci:

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Cont

/etc/X11/xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I've tried several proposed solutions (many ending up with the frozen black screen at boot) and have been fortunate lately in backing up my xorg.conf. I've even tried Karma release Alpha-2 but the problem still exists. Can anyone help? I appreciate any and all suggestions and directions.

---

### Post by Vakman on 2009-07-11
All right, let's see. You say it is not limited to 9.04 so the driver may not be the issue. But we may as well try :)
Ubuntu 9.04 and the Intel driver had some issues.
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
Will show you how to revert to this driver.
If that does not work try following the steps at this link [http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/](http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/)
Hope this helps.

---

### Post by imwithid on 2009-10-14
Moving to the Alphas and Beta of Karmic Koala solved this problem. Now if they can only solve the screen brightness problem, I would consider the release greatly improved on the graphics front.

---

