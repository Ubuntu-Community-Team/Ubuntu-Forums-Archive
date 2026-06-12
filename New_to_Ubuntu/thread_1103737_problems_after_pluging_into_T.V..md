---
title: "problems after pluging into T.V."
date: 2009-03-23
forum: New to Ubuntu
---

### Post by mysticaltopher on 2009-03-23
I pluged my laptop into my TV (just like I used to in windows) using the S-Video connection, now my desktop effects won't work and even now that my TV is not hooked up under System-->Preferences-->Screen Resolution there is still a secondary display box listed saying Unknown on it. (I have the resolution set to off on the secondary display).  When I first pluged it it it downloaded some drivers (i think they were drivers) and that's what i think messed up the system.  I've been reading through the forums but I'm not sure where to start with tackling this problem...not familiar with xorg.conf or even sure if that's the right place to start, any help would be greatly appreciated...Thanks!!

---

### Post by TCSnyder on 2009-03-23
when it installed the "driver" did it say something about Virtual Screen Resolution?

---

### Post by mysticaltopher on 2009-03-23
Yes, do u know what it is?

---

### Post by TCSnyder on 2009-03-23
yes i have had this problem before,
i will tell you everything graphically but you can do command line either way

use a terminal or alt+f2 and type
```
gksu gedit
```
then open /etc/X11/xorg.conf

then do File=>Save as   xorg.conf.backup      for backup purposes

then open the original xorg.conf and look for a the new monitor
you should be able to tell because in it's subsection it says something like

SubSection "Display"
Virtual 2464 900
EndSubSection

so you will know it is a virtual screen resolution

then reboot your computer good luck

if it doesnt reboot graphically in the terminal type 
```
cd /etc/X11
sudo mv ./xorg.conf.backup ./org.conf
```

that will reload your current settings

---

### Post by TCSnyder on 2009-03-23
also to fix your problem you can type alt+f2 ant enter

gnome-display-properties

and you should be able to reset your graphics but it does not keep    settings on reboot.

---

### Post by mysticaltopher on 2009-03-23
here's what it says:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 800
	EndSubSection
EndSection

do i need to delete the SubSection and save before rebooting? thanks!

---

### Post by TCSnyder on 2009-03-23
Delete that whole monitor, not just the subsection and save. then reboot and you should be good.

p.s. i am guessing you just left out the other monitors if that is the only one do not delete it

---

### Post by mysticaltopher on 2009-03-23
there is a "monitor" and a "screen"....I think it tryed to set my tv as the main display but im using my laptop screen now so im confused?  should i delete the whole screen section? Here's the entire page:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 800
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by TCSnyder on 2009-03-23
yes delete all of the screen

you final file should say 

```
Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection
```

---

### Post by mysticaltopher on 2009-03-23
That fixed it...Thanks TC!

---

### Post by TCSnyder on 2009-03-23
no problem

---

