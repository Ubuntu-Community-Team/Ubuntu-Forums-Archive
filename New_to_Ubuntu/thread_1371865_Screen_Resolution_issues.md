---
title: "Screen Resolution issues"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by darkeye123 on 2010-01-03
Hello again,

One of my friends just converted to ubuntu! While he is loving the new environment and options, there is one thing that is preventing him from enjoying it completely. His desktop resolution is the issue. It will only display in 800X600.

Here is the lspci:
```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02
```

We updated the system and everything, but I just can't adjust the stupid resolution. What should I do?

---

### Post by markjensen on 2010-01-03
Can you post the output of the following command?
**xrandr**

It will list the supported resolutions and frequencies that X has determined your card can handle.

---

### Post by darkeye123 on 2010-01-04
Here it is:
```

Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9  
zach@zach-desktop:~$ 

```

---

### Post by darkeye123 on 2010-01-04
xorg.conf
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dbe"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
	Load  "dri2"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82865G Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by darkeye123 on 2010-01-05
Solved! Well, for the most part. We added some new modes with xrandr.

```
xrandr --newmode "1024x768_60.30"  64.43  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

xrandr --addmode VGA1 1024x768_60.30

xrandr --output VGA1 --auto --mode 1024x768_60.30

```

I just made a bash script to run it on startup.

---

### Post by Harry_Iyer on 2010-01-05
Thank you so much!!!

Helped me solve similar issue with Ubuntu on my laptop

_

---

