---
title: "Screen Resolution Problems"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by azz_from_oz on 2009-09-13
Hey all,

So I'm an absolute newbie when it comes to Ubuntu, though I've picked up a few things. My problem is this:

Before I went to Ubuntu (9.04) I was using XP and my screen resolution was at 1024x768, but when I installed Ubuntu I could not go any higher than 800x600. I would upgrade my video drivers (which are onboard) but I don't know the name of the people who made it and the Device Driver for Ubuntu would not show any drivers at all.

I've read many <i>many</i> threads regarding this problem but I seem to be the only one who has a really screwed up version of Ubuntu. This is what my xorg.conf says:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

I've notice that other people's xorg.conf (who also had resolution problems) had actual figures for the monitor and screen sections.

Is there anyway to remedy my situation? Any and all help would be greatly appreciate.

Cheers

---

### Post by fooman on 2009-09-13
open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
lspci | grep VGA
```

press enter....then post back with the output.

---

### Post by azz_from_oz on 2009-09-13
The output was:

01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

... this is the driver I have to update?

---

### Post by fooman on 2009-09-13
sorry,  i am not sure on the S3 cards as i've never owned one.  hopefully someone will come by who has experience with these and can offer some sound advice.

my guess would be that the driver is already installed and you have to manually configure your xorg.conf to suit the card/monitor.  nvidia and ati provide apps for doing this...i don't think you have that same luxury.

i assume you have already gone to system > preferences > display ...and there are no other options besides the 800x600?

---

### Post by azz_from_oz on 2009-09-13
Yeah, I've already tried that route lol thanks

On the subject of adding in the resolution through xorg.conf, how would you suggest I go about doing this?

I've attempted it before and lost my screen (cueing much angry faces lol). I'm a bit more cautious this time. As I said before, my xorg.conf looks completely different to all the others that I've seen, so is there anyway to manually add in an 1024x768 screen resolution?

Any and all help, as before, would be largely appreciated! =D

Cheers

---

### Post by azz_from_oz on 2009-09-14
Bump

Also, I heard somewhere that xserver might be able to help me with my problems.

Does anyone have any ideas? Please

---

### Post by theozzlives on 2009-09-14
here's one you can try, be sure you backup your old one first:
```
Section "Device"
	Identifier	"Configured Video Device"
       Driver          "VESA"
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

---

