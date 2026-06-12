---
title: "Problem with graphics drivers."
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Muffinabus on 2009-01-31
I may have accidentally messed up my xorg.conf when uninstalling previous drivers.  I've made many attempts at installing the latest ATI drivers, all of which were completely unsuccessful.  The output of my fglrxinfo is as follows: ```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  156 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

aticonfig --initial output: ```
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-14
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

```

And attempting to load the drivers in System > Administrator > Hardware Drivers gives the following error:```
Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid.
```

Any help here?  I'm running Ubuntu 8.10 and have an ATI 1950GT.  The last drivers that I had running were the 8-11's and have tried both the 8-12's and the 9-1's thus far to no avail.  I think I may just need to restore my xorg.conf, but am unsure of how I would go about doing that.

EDIT:  Hmm, maybe I should post my xorg.conf as well, ha.

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "vbe"
	Load  "ddc"
	Load  "freetype"
	Load  "int10"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Option	    "UseFBDev" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "ati"
	Option	    "DRI" "1"
	Option	    "UseInternalAGPGART" "1" ## tinker with 1 or 0, it won't hurt your system, just will check if the internal or the fglrx shipped agpgart works
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Muffinabus on 2009-01-31
Hmm, I seem to have fixed it myself (:  It's working!  For now at least.  I reboot Ubuntu, got a black screen, reboot again in recovery mode, reconfigured the X server, rebooted again, purged my previous driver installation attempts, installed one more time, and all's well!

---

