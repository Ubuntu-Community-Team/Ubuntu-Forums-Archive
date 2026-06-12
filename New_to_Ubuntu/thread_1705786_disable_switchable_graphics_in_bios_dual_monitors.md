---
title: "disable switchable graphics in bios? dual monitors?"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by adduds on 2011-03-12
i'm still really new with ubuntu so forgive me...i just need some help

do i have to disable switchable graphics in bios to use fglrx driver?

i have onboard video and standalone card in my laptop

prior to trying to use dual monitors with ubuntu to use my hd radeon video card in my laptop top i installed the fglrx driver rebooted but got a tty screen after a while mucking around i went into my bios and set graphics from switch able to discrete...this worked for linux

when i boot into win7 switch it back to switchable....it is annoying but its worked but now...i just leave it on discrete now as it works i just can't switch to my onboard to save power

i'm trying to use dual monitors with my laptop i have a vga (or hdmi) out i'm using the vga plug it in restart everything works until i select linux from grub then it turns my laptop monitor off and my other standalone says check cable....

i hope this is enough info to get me some help!


this is my xorg.conf file

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "true"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by adduds on 2011-03-14
could someone please help? just makin sure this thread doesn't get buried thanks

---

