---
title: "Help with the screen resoltuion"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by jose187 on 2009-06-09
I plugged my laptop to the TV, and then i turned off the laptop display, and the TV on - while i watched a film.

Now, when i disconected my laptop, the display stayed at 4:3 and doesn't give the the choice to go back to the original 16:9....

So now i have two wide black column at either side of the screen, and no way to change it - this has never happened before and it was working fine.

Please let me know how to do this..

---

### Post by RedSingularity on 2009-06-10
Post the output of your etc/X11/xorg.conf

---

### Post by jose187 on 2009-06-10
> **Shadow121 said:**
> Post the output of your etc/X11/xorg.conf


Here you go...
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1024 1248
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by jose187 on 2009-06-10
SOLVED!!!

I ran this command and then loged out and back in....it once again gave me the option to go 16:9

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

