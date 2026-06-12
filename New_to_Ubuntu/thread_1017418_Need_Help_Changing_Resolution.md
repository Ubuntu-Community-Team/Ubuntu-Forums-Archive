---
title: "Need Help Changing Resolution"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by noobonastick on 2008-12-21
hi, i need help changing the resolution of xubuntu. I have tried opening /etc/X11/xorg.conf but i dont know where to edit it.
The following is my xorg.conf



> 

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

Note, i cut out the headers

Thanks for helping

---

### Post by nhasian on 2008-12-21
see if this helps you any:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by hunges on 2008-12-21
[THIS]("http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html") worked for me!!!!!!!

Scroll to "Ah , Low Screen Resolution Problem" 

FINALLY!!!!!!!!!!!!!!!!!!

---

