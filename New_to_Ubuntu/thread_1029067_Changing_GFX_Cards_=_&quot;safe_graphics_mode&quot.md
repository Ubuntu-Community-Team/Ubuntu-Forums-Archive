---
title: "Changing GFX Cards = &quot;safe graphics mode&quot;"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-01-03
So I recently just picked up a new laptop so I could have an Nvidia gfx card. So I just finished cloning my hard drive into the new system (with the ATI drivers installed on it) when it booted up in the new laptop I was running in "safe graphics mode" I used envyng-gtk to uninstall the ATI drive and then install the recommended Nvidia driver for my new card. How ever after rebooting it is still throwing me an error about my gfx card and loading into safe graphics mode... is there any way to resolve this with out formatting? (I really kinda just got everything working how I like)

Help!

~Jeff

---

### Post by Perfect Storm on 2009-01-03
```
sudo nano /etc/X11/xorg.conf
```

is the driver set to "nvidia" ?

---

### Post by beastrace91 on 2009-01-03
Here is what it has: ```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:1:0:0"
	Driver	"nvidia"
EndSection

```

Driver is set to nvidia but the rest has ATI every where... what should I change?..

~Jeff

---

### Post by beastrace91 on 2009-01-03
Ok so I am looking around online and I *think* the issue appears to be the new card and not drivers hanging around from the old one...

I found some threads on other places:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843)
[http://ubuntuforums.org/showthread.php?t=784037](http://ubuntuforums.org/showthread.php?t=784037)

And the first one is the exact issue I am having (I have 4 gigs of ram and a 9500M GS...) Going to see if the second thread helps any...

~Jeff

---

### Post by beastrace91 on 2009-01-03
Ok here are the errors it is getting upon boot that cause it to go into "safe graphics mode"

```
(EE) NV(0): Failed to determine the amount of available video memory
(EE) Screen(s) found, but none have a usable configuration.
```

Going to search around and see if I can find a solution online... if anyone has any idea how to resolve this issue your input is welcome!

~Jeff

---

### Post by beastrace91 on 2009-01-03
So I am now truly upset! Apparently the issue as a whole was with having 4 GIGS of ram... not my GFX card at all... I am starting [a new thread](http://ubuntuforums.org/showthread.php?p=6485826#post6485826) a this one implies it is the GFX card causing the issue.

~Jeff

---

