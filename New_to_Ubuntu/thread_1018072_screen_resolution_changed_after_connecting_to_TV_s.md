---
title: "screen resolution changed after connecting to TV screen!"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Anaphylaxis on 2008-12-21
My screen resolution changed after I plugged an RGB cable into my laptop to watch a movie on a plasma screen. 

My laptop should have a 1280*800 resolution. Highest option listed under "preferences - screen resolution" is now 1024*768.

And there is this label displaying "laptop 15" overlapping my "Applications" menu button, preventing me from accessing the menu.

.xprofile doesn't exist. 
xorg.conf contains no relevant information - this is all:
> 
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


HELP!

---

### Post by Anaphylaxis on 2008-12-22
Alright, figured out what I had done wrong. 

I tried to mirror my screen on a TV only capable of displaying 1024*768 (without knowing the max resolution beforehand)

While playing around with the resolutions to get a decent picture, I set the max resolution of my virtual screen to 2000 something * 768. 

This changed the config in xorg. 

I just deleted the xorg.conf line and everything went back to normal.

---

