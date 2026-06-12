---
title: "HDMI Sound Output - Configure?"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by Dark7man on 2011-02-16
Hey all, I haven't posted in a while, I've have a new install of Kubuntu 10.10 (64bit) - I had Ubuntu 10.10 installed previously and thought I'd try out something new as I had quiet a number of issues.  Love the Linux World, I still have a duel boot (Win7) as I'm still ironing out some kinks before its my only OS.  Kubuntu - very impressive!

ANYWAY!

I am connected my laptop (HP - DV6-1340SA) to my HDTV via HDMI.  I can get the video configured to use the TV, however I cannot seem to find the option to change the sound output to HDMI also!
So I have the video on HDTV - sound still coming from laptop speakers!

I think the software in my system tray is KMix - I have tried the menus from the mixer there but it only seems to list one playback device!
"Internal Audio Analog Stereo"

I came across the konsole/terminal command "aplay -l" and here is the output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

That looks to me like it can see some sort of HDMI  device - I guess by part of the name "Intel [HDA Intel], device 3"
does HDA = High Definition Audio" by any question? :)

Anybody any suggestions please?
All help is appreciated!

Many thanks!

---

### Post by Dark7man on 2011-02-16
Can I remove KMix and try installing a different ALSA Config GUI of some sort or is it really a driver/configuration issue?

---

### Post by brawd on 2011-02-16
Best of luck on this bro.

I've been waiting 3 months - since I first installed a HDMI card and during that time tried many 'solutions' but still without.

The galling thing is I tried XP and life was a bowl of cherries.

Evenso I shall still not go back to XP/Vista/Win7 and get costed out of computing.



regards,

---

### Post by Dark7man on 2011-02-17
> **brawd said:**
> Best of luck on this bro.

I've been waiting 3 months - since I first installed a HDMI card and during that time tried many 'solutions' but still without.

The galling thing is I tried XP and life was a bowl of cherries.

Evenso I shall still not go back to XP/Vista/Win7 and get costed out of computing.



regards,

Same here mate :) - Windows is now on the way out for me... as soon as my knowledge and finding my way around and configuring a Linux system is up to speed... bye bye Windows! its a pity to have to switch back to Windows for something so simple, when I'm enjoying Kubuntu so much!

I had this working no problem in Ubuntu 10.10... Simply went into the mixer - think it was pulse (maybe alsa) not too sure... and changed the sound output device to HDMI...  I would imagine if its possible in Ubuntu surely its possible in Kubuntu!

There is bound to be a solution to this... I bet some of the vet's know a thing or two... 

...**BUMP**

---

