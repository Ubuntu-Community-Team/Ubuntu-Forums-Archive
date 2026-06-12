---
title: "32 bit color and web video crashes"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Durendal on 2010-01-17
So yesterday I installed Ubuntu 9.1 via virtualbox on an external hard drive and now I'm having a few problems with it.

First one is when I boot the system virtual box gives me a prompt saying it's optimized for 32 bit color and the guest system is running in 16 bit.  Searching around the net I gathered that 24 bit color is what I want, problem is the ways I've been finding to change that involve editing the xorg.conf file and 9.1 doesn't seem to have that file.

Second issue is when going to websites with video, such as youtube, firefox will load the first frame of video and maybe a split second of sound before freezing and crashing.  Only thing I've been able to find about this is that 2 years ago it was a fairly common problem.  Is there any way to fix this or a different web browser that won't have this issue?

Keep in mind yesterday was my first experience ever with Linux so I'm a bit behind the curve as far as technical knowledge goes.

---

### Post by halitech on 2010-01-17
Did you install the Guest Additions after you installed Ubuntu to enable the video driver?

---

### Post by Durendal on 2010-01-17
Yeah the guest additions were installed right after the ubuntu updater finished.

---

### Post by halitech on 2010-01-17
then you should be able to modify the screen resolution and depth by going to System - Preferences - Display I think.

---

### Post by Durendal on 2010-01-17
In display preferences the monitor is unknown.  I can adjust the resolution (also seems the resizing the virtualbox window automatically adjust the resolution), there's also drop down menus for refresh rate and rotation but no options in those menus.  Don't see anything about depth though :(

---

### Post by halitech on 2010-01-17
if you want to make changes to the xorg.conf file (that has been removed for some reason) then open a terminal and run
```
sudo touch /etc/X11/xorg.conf
```
note: the X11 must be upper case

then to edit it, run
```
gksudo gedit /etc/X11/xorg.conf
```
and you can add what you need

---

### Post by Durendal on 2010-01-17
Thanks for all your help halitech, tried those last two commands and it opens up a completely blank xorg.conf file in gedit.  If it was just editing  a few lines in an existing file I'd be alright with that, but creating one from scratch I'm not too comfortable with that.

---

### Post by halitech on 2010-01-17
by default 9.10 doesn't use xorg.conf any more so you will need to create one from scratch. here is mine

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
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Modes	"1280x1024" "1440x1050"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

You can probably ignore most of it and try just adding the section for Screen and set Identifier, Device and Monitor to Generic and then add the DefaultDepth and subsection for the resolutions.

---

### Post by Durendal on 2010-01-17
Thanks again halitech, that seems to have resolved the color issue.  Any ideas on my second problem with firefox and video?

---

### Post by halitech on 2010-01-17
did you enable the medibuntu repos and install adobe flash?

---

### Post by Durendal on 2010-01-17
Flash was installed but I didn't know about the medibuntu repositories, with those I'm now getting about 10-15 seconds of video before firefox crashes.  Some improvement but not quite there yet.

---

