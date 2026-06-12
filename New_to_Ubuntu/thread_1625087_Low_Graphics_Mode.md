---
title: "Low Graphics Mode"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-11-18
I'm trying out kubuntu, but it can't seem to automatically configure xscreen. When I boot the computer, it forces me to run in low graphics mode. Anyone know how to fix this?

```
$ lspci

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
01:05.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

```

```


xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



```

Thank you!

---

### Post by papibe on 2010-11-18
Have you tried to use the "Nvidia X Server Settings" program to change the resolution?

When you use the nvidia driver, the regular gnome/kde monitor preferences don't work very well.

Good Luck!

---

### Post by EnigmaticCoder on 2010-11-18
nvidia-settings wasn't installed, so I figured I needed to install the driver. An old driver was installed, so I switched to the new one. Then I rebooted the computer and the problem ceased. Thank you.

---

