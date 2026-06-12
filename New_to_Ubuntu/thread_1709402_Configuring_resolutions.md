---
title: "Configuring resolutions"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by madap on 2011-03-18
I'm fairly new to ubuntu and Linux but always been fascinated by it and definitely want to learn and expand my knowledge about it.

I've been having a bit of a problem with my 22" Asus screen. For some reason, neither windows or ubuntu are recognizing or reading the EDID quite well (or at least that's my conclusion) because they're not getting the native resolution. Or maybe it's the ATi drivers. 
On windows it's just a matter of opening the ATI catalyst center and disabling the option to read the EDID, forcing the res to my native and badaboom that's that. 

Obviously I'm having a bit more trouble in ubuntu.

Here's the basic data:

GFX card: Asus HD4890 1GB DDR5
Monitor: Asus VW223B , native resolution 1680x1050

What I did so far:

I followed several guides on how to obtain your own resolution.
I was successful in getting it to display the resolution in this session but I'm afraid it's gonna be lost once I log out or restart the computer.
Here's what I did...

```
~$ cvt 1680 1050
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

```

For some reason my connected display is recognized as CRT1 (as shown by xrandr -q )
So:
```
~$ xrandr --newmode "1680x1050_60.00" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
~$ xrandr --addmode CRT1 1680x1050_60.00
```

After all this, the resolution shows in my available display resolutions in the normal GUI (System -> Preferences -> Monitors)

Now I want it to be the default mode for every log in, obviously, as it's the correct resolution and everything looks fine.

For that it was suggested I edit xorg.conf but it seems ATi had some fun with it already and it's a hot mess I barely understand.

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x1200"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

I trimmed it down to:

```
Section "Monitor"
	Identifier  "CRT1"
	Modeline    "1680x1050_60.00" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050_60.00"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Radeon 4890"
	Driver      "fglrx"
	Option	    "CRT1" "CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Primary Screen"
	Device     "Radeon 4890"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	2048 2048
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen         "Primary Screen"
EndSection


```


Can someone go through the changes I made and tell me if my computer is gonna explode the next time it boots?

Thanks for your assistance in advance.

---

