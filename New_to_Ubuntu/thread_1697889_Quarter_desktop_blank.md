---
title: "Quarter desktop blank"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by rockoprem on 2011-03-01
Hi all,
I installed some updates today on 10.10 and on reboot my desktop is about a quarter black from bottom. My login screen looks perfectly fine. I tried with my other accounts and I face the same problem. Here is the output from xorg.conf
```


Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "Samsung SyncMaster"
	HorizSync       30.0 - 81.0
	VertRefresh     56.0 - 60.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	Option         "TwinView" "0"
	Option         "metamodes" "nvidia-auto-select +0+0"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
	Option         "Xinerama" "0"
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "Unknown"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Whenever I try to open a new window, xorg has started to hog on my cpu... so says my conky!

Any help?? Please!!

---

