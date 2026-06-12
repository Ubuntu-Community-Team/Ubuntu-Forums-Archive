---
title: "Screen rotation for Portege 3500 (trident video card)"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by littlematt on 2009-01-07
Hi all

I've recently installed ubuntu hardy heron on my portege 3500 tablet PC, but I can't get screen rotation to work. Typing RandR into terminal returns command not found. My xorg.conf is attached.


Serial wacom tablet (working)
Graphics card: Trident CyberALADDiN-T Graphics accelerator

Any help/advice appreciated.

littlematt

---

### Post by gettinoriginal on 2009-01-15
Sorry, but I cannot open your Xorg :confused: but I do have this for you to try:

```
sudo gedit /etc/X11/xorg.conf
```

and add
Option "RandRRotation"
so it looks like this.

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
Option "NoLogo" "true"
Option "RandRRotation"
EndSection

---

### Post by littlematt on 2009-02-08
> **gettinoriginal said:**
> Sorry, but I cannot open your Xorg :confused: but I do have this for you to try:

```
sudo gedit /etc/X11/xorg.conf
```

and add
Option "RandRRotation"
so it looks like this.

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
Option "NoLogo" "true"
Option "RandRRotation"
EndSection

Hi

Sorry about the delay in relping, your help is appreciated!


The part of my Xorg.conf which I think is equivilent to your suggestion is:

```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Trident CyberBlade (generic)"
	Busid		"PCI:1:0:0"
	Driver		"trident"
	Option		"RandRRotation" "CW"
	Screen	0
	Vendorname	"Trident"
EndSection
```


I think the reson I'm having problems is my card isn't nVidia (or radon), it's Trident (which I had never heard of untill I tried to get ububtu to work!)

I've tried removing the "CW" from the line in my xorg.conf, but has no effect. What does the CW mean anyway? Clockwise?


Thank you for any help,
littlematt

---

### Post by Favux on 2009-02-08
Hi littlematt,

Yes CW means clockwise.  Instead of CW you should have "True" or "on".

Please see gorcq's thread:

[http://ubuntuforums.org/showthread.php?t=1053210]("http://ubuntuforums.org/showthread.php?t=1053210")

And also this bug repot:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312")

It would probably be a good idea for you to join gorcq in making a report on the bug page.

---

