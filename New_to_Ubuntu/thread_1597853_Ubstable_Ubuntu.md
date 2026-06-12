---
title: "Ubstable Ubuntu?"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Fast_light on 2010-10-15
[COLOR=#000]Dear friends,[/COLOR]
 
Till this day I have always been an avid windows user. I am a Second Life user on Windows, but because windows always crashes, I decided to get started with Ubuntu. I am a real beginner when it comes to Ubuntu.
 
It seems that Ubuntu is not very stable on my computer. After a easy installation, soon there came some nasty problems. I have installed Phoenix (a secondlife viewer for linux) After installing, I created a shortcut, but for some reason sometimes the shortcut does not work. I receive an error "can not find the file, it's not exist" or something like that. after a reboot suddenly the sortcut works, but de next day it doesn't work.
 
The other problem is more serious, perhaps to difficult for a beginner'...... on the internet are many forum questions asked about this problem, but unfortunately no solution for me. I have an Audigy2 card (SB0240) but I do not get this to work. After many attempts I finally bought a cheap 5.1. sound card. This one worked right away, but no 5.1. sound. Sometimes the sound isn't work at all and I must reboot the PC after a reboot the sound is back (still no 5.1). Does anyone have a suggestion? I really tried very much but unfortunately still unresolved. It seems like Ubuntu is not stable.... because it gives "sometimes" problems

---

### Post by QIII on 2010-10-15
Neither the performance of any application nor the function of particular hardware is a commentary on the OS.

If apps don't work, it is the responsibility of the developer.

If hardware doesn't work, the OEM is responsible for drivers.

Microsoft supports neither third party software nor third party harware.

Developers and OEMs ensure their products work with Windows.  Not the other way around.

I would start two new threads -- one for each of your issues independently.

---

### Post by earthpigg on 2010-10-15
The Phoenix problem sounds like a Phoenix problem -- I suggest checking out their support forums.

For the sound card, I suggest returning it. In the future, check for Ubuntu/Linux compatibility ***before*** purchasing hardware. My general solution to hardware problems is that if I don't see nearly unanimous statements that it works perfectly on Linux, I don't purchase it.

---

### Post by clhsharky on 2010-10-15
Fast_light

If you are having issues with windows and Ubuntu, might indicate hardware failing.
Test memory with live CD.
Could also be power supply stability.

Sharky

---

### Post by sandyd on 2010-10-15
> **Fast_light said:**
> [COLOR=#000]Dear friends,[/COLOR]
 
Till this day I have always been an avid windows user. I am a Second Life user on Windows, but because windows always crashes, I decided to get started with Ubuntu. I am a real beginner when it comes to Ubuntu.
 
It seems that Ubuntu is not very stable on my computer. After a easy installation, soon there came some nasty problems. I have installed Phoenix (a secondlife viewer for linux) After installing, I created a shortcut, but for some reason sometimes the shortcut does not work. I receive an error "can not find the file, it's not exist" or something like that. after a reboot suddenly the sortcut works, but de next day it doesn't work.
 
The other problem is more serious, perhaps to difficult for a beginner'...... on the internet are many forum questions asked about this problem, but unfortunately no solution for me. I have an Audigy2 card (SB0240) but I do not get this to work. After many attempts I finally bought a cheap 5.1. sound card. This one worked right away, but no 5.1. sound. Sometimes the sound isn't work at all and I must reboot the PC after a reboot the sound is back (still no 5.1). Does anyone have a suggestion? I really tried very much but unfortunately still unresolved. It seems like Ubuntu is not stable.... because it gives "sometimes" problems
```

sudo apt-get install alsa-firmware linux-firmware linux-backports-modules-alsa-generic 
```
One of those packages should enable your card

> **earthpigg said:**
> The Phoenix problem sounds like a Phoenix problem -- I suggest checking out their support forums.

For the sound card, I suggest returning it. In the future, check for Ubuntu/Linux compatibility ***before*** purchasing hardware. My general solution to hardware problems is that if I don't see nearly unanimous statements that it works perfectly on Linux, I don't purchase it.
No! don't return it!!!!
[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

---

### Post by jkxx on 2010-10-15
sandyd's advice just above will probably get your sound working. If not, you can try a couple other things.

First, try launching the program 'pavucontrol' and selecting 5.1 sound - if it's not installed, install it first through synaptic.

Second, ALSA tends to... have problems with various cards, so you have another option called OSS to try. The guide for that is at [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound"), follow it and you'll likely have sound work with either of your sound cards.

Try these in order though, with the OSS route only if all else fails.

---

