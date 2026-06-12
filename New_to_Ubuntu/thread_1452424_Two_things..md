---
title: "Two things."
date: 2010-04-11
forum: New to Ubuntu
---

### Post by themarker0 on 2010-04-11
I'm trying to get sound on my laptop working before the 29th of this month. Its actually quite important i do.

First i want to know what it means here
[http://www.linlap.com/wiki/acer+aspire+timeline+5810t](http://www.linlap.com/wiki/acer+aspire+timeline+5810t)

under sound. Will that make the mic work?

I need to feed an input to the mic (From a DI) to record something. i assume to test i could just use my ipod and a doubesided cable non? 


Also, how to i install UVC?

---

### Post by WinterRain on 2010-04-12
> **themarker0 said:**
> 
Will that make the mic work?


Only one way to find out.
```
use model=acer on snd_hda_intel module
```
What's UVC? Video capture? If so, it is in synaptic.

---

### Post by themarker0 on 2010-04-12
> **WinterRain said:**
> Only one way to find out.
```
use model=acer on snd_hda_intel module
```What's UVC? Video capture? If so, it is in synaptic.

No command found.

Also i will try thank you.

---

### Post by themarker0 on 2010-04-13
Bump.

---

### Post by Don1500 on 2010-04-13
try this:
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

Sure, it says 9.04, but it works for 9.10, too.

---

### Post by lyall on 2010-04-13
have you installed** Gnome Alsa mixer** from Synaptic Package Manager
look for **alsamixergui**

then check the setting to see if any are muted

if you are still having problems check the Community Documentation for 
SoundTroubleshooting [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

if still having problems check he Community Documentation for Sound
[https://help.ubuntu.com/community/Sound]("https://help.ubuntu.com/community/Sound")
 then click on HdaIntelSoundHowto

hope this helps you

good luck and have fun learning

---

### Post by 3rdalbum on 2010-04-13
UVC is a driver for standards-compliant video sources, such as webcams. It is already in the kernel and will activate when a UVC device is plugged in.

---

### Post by lidex on 2010-04-14
> **WinterRain said:**
> Only one way to find out.
```
use model=acer on snd_hda_intel module
```
What's UVC? Video capture? If so, it is in synaptic.
The way to implement this:
In a terminal="Applications>Accessories>Terminal" enter
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
to open the file for editing. Add this line at the bottom:
```
options snd-hda-intel model=acer
```
Save. Close. Reboot.

---

### Post by themarker0 on 2010-04-14
> **lyall said:**
> have you installed** Gnome Alsa mixer** from Synaptic Package Manager
look for **alsamixergui**

then check the setting to see if any are muted

if you are still having problems check the Community Documentation for 
SoundTroubleshooting [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

if still having problems check he Community Documentation for Sound
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
 then click on HdaIntelSoundHowto

hope this helps you

good luck and have fun learning

I will try this thank you.

> **Don1500 said:**
> try this:
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

Sure, it says 9.04, but it works for 9.10, too.

I will try.

> **lidex said:**
> The way to implement this:
In a terminal="Applications>Accessories>Terminal" enter
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```to open the file for editing. Add this line at the bottom:
```
options snd-hda-intel model=acer
```Save. Close. Reboot.

I added it under this line, just making sure its right.

```
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

```

---

