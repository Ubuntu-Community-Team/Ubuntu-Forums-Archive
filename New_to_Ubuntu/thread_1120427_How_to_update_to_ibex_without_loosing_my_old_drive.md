---
title: "How to update to ibex without loosing my old drivers?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by powel212 on 2009-04-09
Trying to run Ubuntu on my friends old Toshiba Satellite A20. The hardware inside is very old and somewhat proprietary. It is still a decent machine though.

It runs fine when I install Gutsy and then upgrade to Hardy but when I update to ibex I lose all the drivers. USB support, Lan support, sound card support all disappear after the ibex upgrade.

I could keep it in Hardy Heron but I would prefer ibex. 

Is there a switch that will allow updating to ibex OS and force the upgrade to leave the old drivers in place?

Thanks for any help

Powel

---

### Post by jeremyjjbrown on 2009-04-09
Most linux drivers are kernel dependent. You should update your drivers for each version of Ubuntu. Trying to keep them will only cause problems, most of which can be avoided by a clean install.

---

### Post by Sef on 2009-04-09
I would run the Ibex live cd and see if there are any problems with it.  If there are, then there will most likely be the same problems upon install.

---

### Post by powel212 on 2009-04-09
I see. I had originally tried to install a clean copy of ibex but it didn't support many devices inside the box. I should have mentioned that. My mistake. 

When I started with Ibex there were just too many unsupported devices inside the old box so I was unable to manipulate it or make changes to get it to work at all. So I switched to the older Gutsy install and then most everything worked. But I prefer the ibex interface so had hoped too update it from Gutsy to Hardy and then to ibex. 

I have it running Hardy now so I will fool around with it and try to tweak it to my liking. 

Thanks for the feedback.

Powel

---

### Post by powel212 on 2009-04-10
how i solved the problem of video driver on Toshiba Satellite A20

Fresh install of ibex

copied the following into my xorg.conf

```
Section "Device"
 Identifier "Configured Video Device"
 Boardname "Trident CyberBlade (generic)"
 Busid "PCI:1:0:0"
 Driver "trident"
 Screen 0
 Vendorname "Trident"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
 Vendorname "Generic LCD Display"
 Modelname "LCD Panel 1024x768"
 Horizsync 31.5-48.0
 Vertrefresh 56.0 - 65.0
 modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
 Gamma 1.0
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 Defaultdepth 24
 SubSection "Display"
  Depth 24
  Virtual 1024 768
  Modes "1024x768@60"
 EndSubSection
EndSection
```

Now all devices are recognized and I have full display support to 1024X768

Sweet

Powel

---

