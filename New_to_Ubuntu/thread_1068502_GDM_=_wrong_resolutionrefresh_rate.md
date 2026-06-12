---
title: "GDM = wrong resolution/refresh rate"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by nadster on 2009-02-13
I'm using ubuntu 8.10, I've setup an automatic login, however it still pops up during boot with a brown square that is off centered. This is because it is using another resolution/refresh rate independent of what is setup once you login. (I tried without an automatic login and the login displays similarly to that brown square off center on the screen)

In ubuntu 8.10 how does one setup a machine to display the same resolution and refresh rate on the login as compared to the settings within ubuntu.

Yes I've searched several times for several different machines that this occurs on but I've never found anything concrete.
If somebody could please explain why this behavior exists that be great too. 

As well my xorg.conf is completely blank, should I be concerned.

Thank you for any help/advice.

---

### Post by loboc on 2009-02-13
xorg.conf has been slimmed down by default but it still can be used to set monitor display settings

this command should give you all the xorg.conf questions instead of the new slimmed down one.

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

You can mannually edit xorg.conf too.
After either of theses steps it should look like this

> # THIS IS FOR MY 20" G5 iMAC - change accordingly!
# FPDithering is only for nv driver and lcd screens

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync       28-84
        VertRefresh     43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
 	SubSection      "Display"
       		Depth   24
       		Modes   "1680x1050"
       	EndSubSection
EndSection

Section "Module"
        Disable "glx"
        Disable "dri"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nv"
	Option	"FPDither" "true"
EndSection

The important part is 

Section "Monitor"
	Identifier	"**Configured Monitor**"
        HorizSync       28-84
        VertRefresh     43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"**Configured Monitor**"
	Device		"Configured Video Device"
	DefaultDepth	24
 	SubSection      "Display"
       		Depth   24
       		Modes   "1680x1050"
       	EndSubS

---

