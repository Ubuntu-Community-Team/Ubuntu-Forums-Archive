---
title: "Dual Monitor setup ATI + Onboard Intel Card in Gutsy or Hardy"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by pmains on 2008-12-11
I am interested in getting a dual-monitor set up on my work computer. I had it working in Feisty Fawn, but the xorg.conf we created didn't work in Gutsy. We have an onboard Intel video card, and an ATI Radeon RV100 card.

I'm sure this question has been answered on these forums before, but there's so much noise, it's difficult to find a clear answer to this (probably common) question. I could "experiment," but I don't really know where to start, and I can't afford to blow hours and hours of work time on playing with something that I have no real knowledge of.

Is this better supported/handled automatically in Intrepid Ibex? My coworker has the same problem in Hardy Heron. He was able to find the Feisty solution after much trial and error.

Now a (I hope polite) disclaimer: Please don't respond with, "I don't think that's possible." It worked in Feisty. It's possible. I noticed that many people asking about this in other threads got that response over and over again. Those sorts of posts clutter the forum and make looking for answers a frustrating experience.

Here's what I believe to be the last working xorg.conf I had under Feisty. (There's another one, but it's rather similar, so this should give you an idea.)

[INDENT]Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	16
	SubSection "Display"
		Depth	16
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 865"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection[/INDENT]

---

### Post by ohzopants on 2008-12-11
The first thing I would do is set the server layout section to only use one of the two monitors and make sure that both work independantly (e.g. set it to use only the one attached to intel, restart X, make sure it works, repeat with monitor attached to ati).

If they do both work independantly, than all you need to do is figure out how to properly set the "screen 0 "screen1" 0 0" line.

Ibex ships with (I think) DisplayConfigGTK.  It's a GUI utility to set these things up.  There might be a backport of it available, but since Ibex uses a more recent X that might not be feasible.

P.S.: In some cases this REALLY isn't possible.  In my pc, for instance, the onboard video is disabled when a pci-e video card is detected.  Obviously your mobo can handle it since you've done it before, but I just wanted to clarify why the "it's impossible" response is so common.

---

