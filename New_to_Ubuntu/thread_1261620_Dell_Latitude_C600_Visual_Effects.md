---
title: "Dell Latitude C600 Visual Effects?"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by seedlings on 2009-09-08
(How) can I use the Visual Effects for this C600?  

System>Preferences>Appearance>Visual Effects Says "Desktop effects could not be enabled".  Can you help me find the correct driver, or should I just fogettaboutit on this old machine?

Thanks,
CHAD
----------------------------------

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by nandemonai on 2009-09-09
I'm fairly sure support has been dropped for that card by ATI (ATI Technologies, Inc. Rage Mobility M3 (AGP)") which will likely mean you wont get 3D acceleration. You can check by looking in System - Administration - Hardware Drivers.

If nothing shows up there, you may be out of luck.

I'm not sure, but you _may_ be able to get 3D support with a newer version of the open source drivers but don't quote me on that ;)

---

### Post by seedlings on 2009-09-09
Any suggestions for streaming video?  Myeasytv.com won't play and stupidvideos.com is choppy.  Youtube seems OK.

CHAD

---

