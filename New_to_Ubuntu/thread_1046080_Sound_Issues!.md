---
title: "Sound Issues!"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by neigun on 2009-01-21
Hi Guys

well I'm getting to grips with Ubuntu and very rarely need or want to boot into XP anymore- so thanks for the support.

At the moment I'm having trouble installing sound effects into the Gnome desktop environment and playing sound via Firefox. The Gnome mixer I tried recognised all three cards on my system, i.e. SB, ATI AGP & motherboard but kept coming up with error messages- so I ditched it in favour of another Alsa mixer.

Currently installed is the Alsa Volume control installed, SBLive 5.1 (SB0060) (Alsa mixer), and I think all the relevant Pulse Audio software. 

The Forums seem to raise this issue, or similar ones, fairly regularly. Is there a current 'How to'- to fix these issues on the forums?

TTFN Neil

System Spec

Ubuntu 8.10 64 bit
Kernel 2.6.27-9-generic
AMD 64 3200
ATI Radeon HD 3650 AGP
1.25Gb Ram
SB Audigy 5.1 PCI

---

### Post by blueridgedog on 2009-01-21
Are you saying you have three audio type cards/devices?  As a rule I have always disabled the on-board sound when installing a expansion card like your SB.

---

### Post by neigun on 2009-01-22
> **blueridgedog said:**
> Are you saying you have three audio type cards/devices?  As a rule I have always disabled the on-board sound when installing a expansion card like your SB.

You are right. 

How do I go about disabling the sound aspect of the ATI card and the onboard graphics in Ubuntu?


Neil

---

### Post by blueridgedog on 2009-01-22
> **neigun said:**
> You are right. 

How do I go about disabling the sound aspect of the ATI card and the onboard graphics in Ubuntu?


Neil

For the onboard card, go into your BIO (how to do this differs for each motherboard, but typically you hit Delete when the system is booting).  You want to look for "onboard peripherals" or similar.  Find the onboard audio and select disable.

I don't know how to do the same with the ATI device as I too have that problem, but have not researched it yet.

---

### Post by neigun on 2009-01-22
> **blueridgedog said:**
> For the onboard card, go into your BIO (how to do this differs for each motherboard, but typically you hit Delete when the system is booting).  You want to look for "onboard peripherals" or similar.  Find the onboard audio and select disable.

I don't know how to do the same with the ATI device as I too have that problem, but have not researched it yet.

Its odd but the onboard audio is disabled already in the BIOS but shows as a selection in the Control Centre sound option.

Neil

---

### Post by markbuntu on 2009-01-22
You don't really need to disable any of your sound devices, you just need to configure everything properly. There is info and links here for just about everything you need to get your sound dialed in


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by neigun on 2009-01-23
:D

Thanks- much appreciated.

I had to install a package in Synaptic and Gnome Alsa Mixer throws up error messages so I'm using another package. But I now have sound in both Firefox and Rhythmbox.

Part of the problem was Pulse was defaulting to the ATI card, so I had to change it to the SoundBlaster by moving the stream in the Pulse Audio volume control.

---

