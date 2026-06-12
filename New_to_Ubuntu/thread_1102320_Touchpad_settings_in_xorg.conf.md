---
title: "Touchpad settings in xorg.conf"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by specialedster14 on 2009-03-21
I'm a new ubuntu eee user (as of 3 days ago) and the first thing I did was fix a couple of bugs I noticed, but there is one thing I cannot seem to figure out.  I want to be able to edit the options for my synaptics touchpad on my eee pc and after some searching it seems the best way to do this is through the xorg.conf file.  However, after checking out my xorg.conf file there is hardly anything in there and definitely no section for my touchpad. 

Here is my xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Why is this so basic compared to most others I see out there and how do I get mine to recognize my touchpad so I can edit the settings?

---

### Post by Temposs on 2009-03-21
Ubuntu doesn't use xorg.conf very directly for hardware configuration anymore. It's done on another level.

To configure your touchpad, you should download the Synaptics Touchpad Configuration GUI, which is in the repositories.

In the Add/Remove program or Synaptic Package Manager program, search for Touchpad, and the GSynaptics program will show up. Install that and configure your touchpad.

Also, Ubuntu-eee(if that's what you're really using) is now known as Easy Peasy, and you can get the newest version at [http://www.geteasypeasy.com](http://www.geteasypeasy.com)

---

### Post by Armor Nick on 2009-03-21
I learned this one by skimming through the arch docs. Xorg uses evdev now, which automatically sets all the configuration for all input modules. That is, it leaves it to the part of the system that controls all the hardware.

---

### Post by Temposs on 2009-03-21
Also, Easy Peasy has its own forums. If you're using this version of Ubuntu, they have their own set of forums that might serve this specific distro better.

---

