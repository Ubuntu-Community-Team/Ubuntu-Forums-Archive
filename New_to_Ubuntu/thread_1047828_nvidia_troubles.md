---
title: "nvidia troubles"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Shpadoinkle on 2009-01-22
noob here. so i had a little tard moment and messed up my xorg.config without making a backup. basically, my screen resolution will only go up to 800 * 600. ive seen alot of people with the same problem, but no solution that works for my situation. heres the way its configured at the moment. heres some specs... using nVidia GeForce 7050/nForce 610i with intrepid. any help?

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

---

### Post by Garyhans on 2009-01-22
Nvidia **** Need more info. Try booting into recovery mode.. and typing sudo xfix if you using 8.10.  Secondly.. Get Nvidia-Settings..  from.. Synaptic.. and run it as sudo only after you are satisfied with the settings..  your resolutions are there.

---

### Post by 2hot6ft2 on 2009-01-22
Go to
System>Administration>Hardware Drivers
and make sure the driver is both installed and active. If not install and/or activate it.
Reboot & check
System>Administration>Hardware Drivers
again to make sure it's active. If it is continue to
System>Preferences>Screen Resolution
to set the Screen Resolution

If it's installed and active but you still can't set it reboot and choose the
Recovery option, at the next menu choose the last option xfix, once it finishes choose the first option to boot normally.
Then set your resolution.

Once the driver is installed you can install nvidia settings manager using
```
sudo apt-get install nvidia-settings
``` in a terminal
Applications>Accessories>Terminal
then you can use ```
gksudo nvidia-settings
``` so you will be able to save the settings when using it.

---

### Post by Shpadoinkle on 2009-03-03
bingo bango 2hot6ft2. i guess i just erased the hardware drivers. reinstalled them and back to normal.

---

### Post by zero244 on 2009-03-04
Glad you got it back.
Ubuntu has improved things in regard to video drivers.
Getting the drivers, resolution running correctly can be difficult.
Its getting easier with every release.
Its funny sometimes the drivers install without a hitch and sometimes you need to tweak things.
A small price to pay for a great OS.

---

