---
title: "Desktop ACER AL2216W LCD Monitor Brightness - Cannot Adjust (Intel 965 Graphics)"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by imwithid on 2009-06-26
I've made attempts for days trying to find a way to change the brightness output to my ACER AL2216W. It is set to it's lowest point on the monitor itself but it is still too bright. I need sunglasses when I read. I can adjust the brightness through Windows XP using the Intel driver for Windows but cannot do so through Ubuntu. The brightness applet does not work. It has not worked ever! Can anyone suggest a solution?

Here is my hardware profile and xorg:

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
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

and

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

Any help would be greatly appreciated.

---

### Post by Vakman on 2009-07-11
Intel driver. It worked so well with the previous version of Ubuntu. There were issues with these drivers at release. Interesting how the brightness applet is not working though. Let's assume it is the driver. Follow this [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
That should help you, it will show you how to revert to that driver.
Also try [http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/](http://www.ivankristianto.com/2009/06/howto-fix-ubuntu-jaunty-904-intel-graphics-problem/) (if the above does not work)
That is actually a monitor I own for my 3rd desktop. (nVIDIA 9600 GT is my video card)

---

### Post by imwithid on 2009-07-28
I will try this in the next couple of days. I'm in the process of backing up all my data and will try it on a fresh install. I'll post my progress. Thanks for the reply.

---

### Post by Vakman on 2009-07-30
All right, sounds like a plan.

---

### Post by imwithid on 2009-10-14
I've tried this on a fresh install and I've also tried Alpha-2, Alpha-4, and Beta Karmic Koala. The brightness applet has never worked for me (I've tried it on three different laptops and two desktops). The function keys work, however in the case of the laptops without difficulty.

The issue here are the LCD monitors for desktops. They are so bright that it strains my eyes to the point where they blur after about an hour. I put on sunglasses to ease it. This is even after setting the brightness and contrast to 0 using the control panel on the monitor itself.

Is there a file somewhere in the file system where I can alter the brightness directly?

There is no proc/acpi/video folder in my case. Where else can I look?

---

