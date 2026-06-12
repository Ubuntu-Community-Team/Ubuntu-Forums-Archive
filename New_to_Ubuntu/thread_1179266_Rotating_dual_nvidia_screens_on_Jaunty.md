---
title: "Rotating dual nvidia screens on Jaunty"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Tammy82 on 2009-06-05
Hi,

I just finished installing Jaunty and set up the dual monitors using System->Preferences->Display. Then it asked me to install the nvidia drivers, which I did. So I had to set up the dual monitors using the nvidia-settings manager again. However, none of the tools allowed me to specify the rotation of the screens. I tried to add various things in the xorg configuration file and none of them worked. Especially confused I am abou the Virtual display and that the screens are not listed individually. I have the content of my xorg file attached. What changes do I need to make to get one or both screens to rotate?


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	3200 1236
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by mikewhatever on 2009-06-05
I think you need to use the nvidia manager and reset your xorg to the default state.
(sudo dpkg-reconfigure -phigh xserver-xorg) Backup the current xorg just in case you might need it later.

---

### Post by Tammy82 on 2009-06-11
Thanks, but I have tried that. It brings me back to zero, having both screens mirrored. It still does not allow me to rotate the screens.

---

