---
title: "ATI Radeon HD 4350 Graphics Card"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Doublepoppa on 2009-10-24
Ok so Im trying to install this thing and so many things that I try don't seem to work. Either that or it is sooo not newbie Im completely lost. I'm getting very frustrated at reinstalling everything when I get a black screen upon bootup. 

If anyone can provide any help. It would be greatly appreciated. I am very green. Thanks in advance.

---

### Post by 3rdalbum on 2009-10-24
Can you first start by telling us what you've already done. For instance, have you tried using the Hardware Drivers program? Did the driver install through that, or did it not show any drivers for your card? Have you tried installing the driver from the ATI website, and if so did you install "build-essential" and "linux-headers-generic" from the repositories?

---

### Post by halitech on 2009-10-24
I just installed the exact same card on my Debian system and it was a pain as well. I installed it using the ATI driver from the website and I was getting an out of range message due to it jumping the resolution up to 1600x1200 which my monitor didn't support.

Here is a copy of my xorg.conf in case it will help
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
	Option	    "ModelName" "Acer AL1916 LCD Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		[B]Depth     24
		Modes    "1280x1024" "1440x1050"[/B]
	EndSubSection
EndSection

```
the section is bold is what I had to add

---

### Post by Doublepoppa on 2009-10-24
Ok here's some more info about where I'm at. I couldn't find anything in the Hardware Driver program for ATI just NVidia (which I think comes from the poor built in graphics cards on my motherboard). I even tried the program envy or whatever its called that I saw on the internet as a possible solution. 

Finally though I figured out how to use ATI's PDF instructions to install the driver. That worked but at the end of the instructions it says this:

Launch the Terminal Application/Window and run:
   For versions of X.Org newer than 7, /usr/bin/aticonfig --initial  to configure the
   driver for your ATI product.
                                     
For versions of X.Org older than 7, /usr/X11R6/bin/aticonfig --initial  to configure
the driver for your ATI product.

I tried putting in both and got the message "No supported adapters detected"

That seems to say that I didnt install it correctly but everything up to that point seemed to suggest I had and had gone just as their instructions had said. I really don't want to reboot and get a black screen.

---

### Post by Doublepoppa on 2009-10-24
Bump

---

### Post by Doublepoppa on 2009-10-25
sorry but Bump

---

### Post by halitech on 2009-10-25
can you post the output of
```
lspci | grep VGA
```

Is there a way of disabling the onboard video in the BIOS?

---

