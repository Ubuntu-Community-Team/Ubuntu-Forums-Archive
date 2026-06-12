---
title: "Toshiba 4030cdt Display Problems"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by uraliss on 2009-02-26
Hi Folks,
I have tried a number of distributions on my old toshiba 4030cdt laptop and so far all have failed to setup the display correctly (1024x768 ) except the latest version of puppy linux. I can only use 800x600 on all other distributions I have tried, including ubuntu. This is centred in the middle of the screen with black borders round the edges.
I have read somewhere that this laptop can only handle this resolution at a colour depth of 16 ???
What do I need to do to configure ubuntu intrepid ibex to use all of my screen correctly?

many thanks

---

### Post by powder on 2009-02-26
You might want to try a custom modeline.  See this HowTo...

[http://ubuntuforums.org/showpost.php?p=454217&postcount=1](http://ubuntuforums.org/showpost.php?p=454217&postcount=1)

---

### Post by uraliss on 2009-03-05
OK, thanks for the help but I have managed to solve this... for me anyway.

As puppy linux seemed to configure my screen correctly, all I did was copy the xorg.conf from puppy to my laptop and it worked.

here it is just in case it helps anyone else.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option      "XkbRules" "xorg"
	Option      "XkbModel" "pc102"
	Option      "XkbLayout" "gb" #xkeymap0
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto" #mouse0protocol
	Option	    "Device" "/dev/mouse"
	#Option      "Emulate3Buttons"
	#Option      "Emulate3Timeout" "50"
	Option      "ZAxisMapping" "4 5" #scrollwheel
EndSection

Section "Monitor"
	#DisplaySize	  240   180	# mm
	Identifier   "Monitor0"
	VendorName   "TOS"
	ModelName    "5082"
	HorizSync    31.5-48.5
	VertRefresh  40-70
	#UseModes     "Modes0" #monitor0usemodes
	Option      "PreferredMode" "1024x768"
	EndSection
	
Section "Modes"
	Identifier "Modes0"
	#modes0modeline0
EndSection

Section "Device"
	# Available Driver options are:-
	# Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	# <string>: "String", <freq>: "<f> Hz/kHz/MHz"
	# [arg]: arg optional
	#Option     "AccelMethod"        	# [<str>]
	#Option     "SWcursor"           	# [<bool>]
	#Option     "PciRetry"           	# [<bool>]
	#Option     "NoAccel"            	# [<bool>]
	#Option     "SetMClk"            	# <freq>
	#Option     "MUXThreshold"       	# <i>
	#Option     "ShadowFB"           	# [<bool>]
	#Option     "Rotate"             	# [<str>]
	#Option     "VideoKey"           	# <i>
	#Option     "NoMMIO"             	# [<bool>]
	#Option     "NoPciBurst"         	# [<bool>]
	#Option     "MMIOonly"           	# [<bool>]
	#Option     "CyberShadow"        	# [<bool>]
	#Option     "CyberStretch"       	# [<bool>]
	#Option     "XvHsync"            	# <i>
	#Option     "XvVsync"            	# <i>
	#Option     "XvBskew"            	# <i>
	#Option     "XvRskew"            	# <i>
	#Option     "FpDelay"            	# <i>
	#Option     "Display1400"        	# [<bool>]
	#Option     "Display"            	# [<str>]
	#Option     "GammaBrightness"    	# [<str>]
	#Option     "TVChipset"          	# [<str>]
	#Option     "TVSignal"           	# <i>
	Identifier  "Card0"
	Driver      "trident" #card0driver
	VendorName  "Trident Microsystems"
	BoardName   "Cyber 9525"
	BusID       "PCI:0:4:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
    DefaultDepth 16
    Subsection "Display"
        Depth       16
        Modes       "1024x768"
    EndSubsection
EndSection


```

---

