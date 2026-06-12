---
title: "Login Screen Resolution problem.."
date: 2009-01-29
forum: New to Ubuntu
---

### Post by dhaft88 on 2009-01-29
I'm fairly new to Ubuntu and I've figured out how to configure my desktop to the correct res (it was stuck in 1024x768 ), but now I'm facing a login screen res problem.

I've already looked at: [http://ubuntuforums.org/showthread.php?t=151192](http://ubuntuforums.org/showthread.php?t=151192) and [http://ubuntuforums.org/showthread.php?t=359310](http://ubuntuforums.org/showthread.php?t=359310) to no avail, maybe I've missed something? My monitor probably isn't configured correctly but it works for me. I have an acer x203w and a nvidia card configured in the following manner:
```

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 2560x1600"
	Horizsync	31.5-99.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1680x1050@58"	"1600x1200@60"	"1400x1050@60"	"1792x1344@60"	"1280x1024@60"	"1856x1392@60"	"1280x960@60"	"1920x1440@60"	"1024x768@60"	"2048x1536@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"nvidia"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Redache on 2009-01-29
I agree with the post below thinking about it.

---

### Post by smothpocket on 2009-01-29
Have you installed the nvidia drivers? I know the proprietary drivers will configure your xorg.conf for you. It's always worked like a charm for me.

---

### Post by dhaft88 on 2009-01-29
Yeah, they're in use in my Admin -> Hardware Drivers..

---

### Post by Redache on 2009-01-29
Try uninstalling and Reinstalling them.
It should redo your Xorg.Conf.

---

### Post by smothpocket on 2009-01-29
If you do have them installed and want it to automatically configure the xorg for you run sudo /usr/bin/nvidia-xorg ... i believe it was that or something very similar.

---

### Post by dhaft88 on 2009-01-29
I uninstalled them, reinstalled - worked perfectly :rolleyes:. Thank you very much, if only I knew before it was that simple...

---

### Post by linfidel on 2009-01-29
I don't know if this applies to your situation, but in case it does...
I found that I have problems if my monitor is not turned on and connected when I first boot (I have a KVM switch, so it is sometimes on but not connected).  The startup wants to detect the monitor (possibly an NVidia feature), and if it doesn't, it will often choose a lower resolution.

I used to just press Ctrl-Alt-Backspace (restart X) when I noticed the login screen was low-rez; but I've had another ongoing problem that this doesn't fix - my mouse scroll-wheel misbehaves in Firefox, causing the history to scroll instead of the page.  I'm not sure if this happens when the mouse is not connected (because of the KVM switch), or the monitor is turned off (sounds unlikely, but may well be the case).

Sometimes, it seems like the resolution is wrong even when the monitor is on, but has been in standby, but I'm not sure yet.

---

