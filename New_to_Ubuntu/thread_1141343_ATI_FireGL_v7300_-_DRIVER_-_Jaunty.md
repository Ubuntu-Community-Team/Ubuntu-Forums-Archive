---
title: "ATI FireGL v7300 - DRIVER - Jaunty"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by aas452 on 2009-04-28
I am having trouble with my ATI Driver, it seems like I am getting an error at start up which forces me to boot in low graphics mode.

I followed the directions on [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) but had no luck

Maybe someone can give me a hand - 

My xorg.conf file

```


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:5:0:0"
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

These are the errors I get when I do frglxinfo in the terminal

```

Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Error: couldn't find RGB GLX visual!

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server " &#65533;&#65533;"
      after 10 requests (9 known processed) with 0 events remaining.

```

---

### Post by aas452 on 2009-04-28
anyone know what is going on, been going through posts all day and cant seem to make sense of anything

---

### Post by Didius Falco on 2009-04-28
> **aas452 said:**
> anyone know what is going on, been going through posts all day and cant seem to make sense of anything

You won't be able to use the proprietary driver for the ATI FireGL v7300 in Jaunty.

I just went to the ATI driver site, and the latest version listed for that card is v8.583. It also states that it supports X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2 and 7.3. 

ATI just dropped a whole range of older cards from their supprt list to the legacy support list. What that means is that they will only release bug-fix drivers for that card, no enhancements.

Jaunty uses X.org 7.4, so the driver isn't going to work in Jaunty at all.

What you need to do is uninstall that driver completely, go into Synaptic and install "xserver-xorg-video-ati" which is the Open Source driver.

The Open Source Driver will work just fine in 2D, but currently has no 3D support. That means no efffects or Compiz.

The Open Source developers  are working on getting the 3D enabled, but it isn't working at this time.

Your options are to either:

1. Uninstall the proprietary driver you installed and install the "xserver-xorg-video-ati" driver and use 2D until they get 3D working.

2. Reinstall Ubuntu 8.10.

3. Get a newer, supported video card.

BTW, I went to the website you linked, and it says right at the top: 
**> Installation Guide for Ubuntu Jaunty (v 9.04) Currently Doesnt WORK!! Be Forewarned...**


Not great news, but still, hopefully, better than being in limbo

---

### Post by aas452 on 2009-04-28
Is there a way to down-grade to 8.10 without losing all my prefrences and software??

---

