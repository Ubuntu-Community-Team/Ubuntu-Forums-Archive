---
title: "Set to screen resolution to 1920x1080"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by aeboo on 2009-08-26
Hey there!

I just got my new Syncmaster 2233sn tft monitor and I would like to use it at 1920x1080. Unfortunately, the GNOME screen settings dialog only offers resolutions up to 1280x1024.

My xorg.conf looks pretty empty:
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
EndSection
```

Can somebody point me into the right direction?

Cheers
aeboo

---

### Post by zerhacke on 2009-08-26
You need to find the maximum resolution supported by your video card.  Getting a monitor that can do a billion by a billion will not do it if your video card won't do it.

---

### Post by GrumbleNZ on 2011-08-31
I have a similar but different problem. I have a Viewsonic 27" 1920x1080 monitor but when I set the screen res to 1920x1080 the desktop edges 'fall off' the page. How can I set Ubuntu desktop to display in 16:9 rather than 4:3 ratio?

Thanks!!

---

### Post by overdrank on 2011-08-31
Hi and please start a new thread for your issue. Thread closed.

---

