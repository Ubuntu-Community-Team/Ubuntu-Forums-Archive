---
title: "How to change resolution for Via S3 unichrome pro IGp"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by mandeepsmagh on 2010-05-10
Hi, guys. I am having problem with resolution, getting max resolution of 800x600. While in windows I can easily get 1024x768.  Have tried OpenSuse and I was getting max resolution of 1024x768 with Vesa Driver. Although video quality wasn't great in full screen. So I m back with Ubuntu again with 10.04. Have tried to generate Xorg.conf to no avail. Please help

---

### Post by mandeepsmagh on 2010-05-10
Finally I was able to create xorg.conf. but it is not used at the moment. 

[PHP]Section "ServerLayout"
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
	Load  "dri2"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
	Load  "record"
	Load  "glx"
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
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa"
	VendorName  "VIA Technologies, Inc."
	BoardName   "K8M800/K8N800/K8N800A [S3 UniChrome Pro]"
	BusID       "PCI:1:0:0"
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
EndSection[/PHP]

There is no section for resolution. Need help to edit it and to get Xserver to use it. Thanks in advance.

---

### Post by mandeepsmagh on 2010-05-11
Still waiting, can someone help me to edit xorg.conf file to get max resolution ? Have tried myself but Xserver crashes and I have to choose the default one.

---

### Post by tubia87 on 2010-05-22
Hi,
have you tried this driver?
[OpenChrome](http://www.openchrome.org/)

---

