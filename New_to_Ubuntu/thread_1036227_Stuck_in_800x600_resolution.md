---
title: "Stuck in 800x600 resolution"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by sonorhC on 2009-01-10
I've recently installed a copy of Ubuntu 8.04 (Hardy Heron) on some decade-old hardware, and I've got a problem with the screen resolution.  If I go to System > Preferences > Screen Resolution, I can select any resolution at all (including ones I know this monitor cannot support--  It should go up to 1024x768), but if I set it to any resolution whatsoever other than 800x600, the scan lines go all wonky and the screen becomes unreadable.  This includes lower resolutions, such as 640x480.

My video card is a VisionTek NV996.0, and my monitor is a Dell VC-10C.  The sections of my /etc/X11/xorg.conf file which appear to be relevant read ```
Section "Device"
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver	"nV"
	BusID	"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option	"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor	"Generic Monitor"
	DefaultDepth	24
EndSection
```
How can I get other resolutions to work?

---

### Post by JoshuaRL on 2009-01-10
Try going to System->Administration->Hardware Drivers.  See if there are any for your card.  And if so, restart your system after and see if that helps.

---

### Post by Kellemora on 2009-01-11
Hi Sonor

Welcome to Ubuntu!

Under Applications OTHER if Screens and Graphics don't come up, RIGHT CLICK on Applications, then select EDIT MENUS.

A box will open up for you to select and place various programs in your Applications OTHER and elsewhere.  Under Other, find Screens & Graphics and place a checkmark in front of it and close that.

Then you will be able to select Applications/Other/Screens and Graphics and set your resolution from there.

I have an article for Screen Resolution I've posted several times, I'm at a different computer and don't have a copy of it here to post for you right now, but if I see you didn't get it worked out or find it, I will tomorrow.

TTUL
Gary

---

### Post by sonorhC on 2009-01-11
**JoshuaRL**:  When I go to drivers, I find a message "No proprietary drivers are in use on this system", and an empty list.

**Kellemora**:  OK, I've added that application, but it didn't seem to be helping directly:  If I set it to a different resolution and hit "test", I get a dialog box (with no window frame) on a scrollable crosshatched background asking me if I want to keep my settings, and if I set a resolution and hit "OK", I get the same problem as when trying to set the resolution through System > Preferences > Screen resolution.

Then, though, I tried using that app to change the model of my monitor (it was showing up as "custom 1").  My specific monitor wasn't listed, and auto-detect just came up with "Plug-and-play", which doesn't work, but I was able to set it to "Dell Super VGA", which seems to work.

With that, I think I've got this problem solved.  Thanks, **Kellemora**.

---

### Post by Bourne_Identity on 2009-01-31
Kellemora,

I don't understand. When I look under Edit--->Menus there is no such thing as Screens and Graphics.

Do you mean Screen Resolution ?

---

