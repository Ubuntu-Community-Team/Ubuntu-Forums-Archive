---
title: "Adding screen resolutions"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by DMonkey08 on 2008-12-17
The highest Ubuntu 8.04 will let me go is 1024x768.  Is there a way I can add 1280x960 to the list?  I know my gfx card can handle it.

---

### Post by tuxxy on 2008-12-17
You could manually add it your your xorg there may be a quicker way depending on which graphics card you use?

---

### Post by samden on 2008-12-17
```
sudo gedit /etc/X11/xorg.conf
``` will let you edit the relevant file. Try adding that resolution to the "Screen" section as per my xorg.conf below:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "1024x768" "800x600"
	EndSubSection
EndSection
``` Then log out and log back in again to see if it worked.

---

### Post by DMonkey08 on 2008-12-17
> **samden said:**
> ```
sudo gedit /etc/X11/xorg.conf
``` will let you edit the relevant file. Try adding that resolution to the "Screen" section as per my xorg.conf below:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "1024x768" "800x600"
	EndSubSection
EndSection
``` Then log out and log back in again to see if it worked.

My xorg file didn't have the "Display" subsection, but I added it in manually and now Ubuntu is running at the correct resolution.  Thanks!

---

### Post by samden on 2008-12-17
You're welcome!

---

