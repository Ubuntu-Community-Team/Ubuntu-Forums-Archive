---
title: "Still having trouble with fullscreen"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by crho85 on 2009-02-24
I am still having trouble with getting any full screen applications to run. I have an ATI 320M card (pain in neck). I have tried using the ATI driver but to no avail.

I do have desktop effects and 3d rendering. But anytime I try to run full screen games or WINE, it logs me out of my session.

see xorg:

```
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
        SubSection "Display"
               Modes             "1024x768"
        EndSubSection
EndSection
```

suggestions?

---

### Post by LowSky on 2009-02-24
this is an issue, with any video card. You cannont run graphic intesive game and Compiz at the same time. there is an option to run something called fusion-icon, that will sit in the system tray and allow you to turn off compiz with ease

---

### Post by crho85 on 2009-02-24
> **LowSky said:**
> this is an issue, with any video card. You cannont run graphic intesive game and Compiz at the same time. there is an option to run something called fusion-icon, that will sit in the system tray and allow you to turn off compiz with ease

as a newb i must ask, how do i turn off compiz

---

### Post by LowSky on 2009-02-24
easiest way without fusion-icon on a blank desktop, right click, go to change background. go to the tab about dektop effect and click on none

---

### Post by crho85 on 2009-02-24
tried this and it did not work, should I try changing driver to ati and then disabling compiz?

---

