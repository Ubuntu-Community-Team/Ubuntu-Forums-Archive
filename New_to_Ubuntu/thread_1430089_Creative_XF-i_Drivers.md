---
title: "Creative XF-i Drivers"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by robbiek01 on 2010-03-14
Hi All does anyone know how to install the creative XF-i drivers I'm not familiar with the command line and can't understand the creative instructions.

---

### Post by robbiek01 on 2010-03-15
> **robbiek01 said:**
> Hi All does anyone know how to install the creative XF-i drivers I'm not familiar with the command line and can't understand the creative instructions.


Below is the instructions i need to follow could someone please help????



====================================================================
 
  Sound Blaster X-Fi Linux 32/64-bit Driver Source Release Readme File 
  September 2008
 
====================================================================
 
The purpose of this document is to describe how to build and install the 
X-Fi Linux device driver. 
 
  
Quick install
 
============= 
In terminal,
 
1) Goto source directory 
2) Execute make command as root 
   make 
   make install 
 
Uninstall 
========= 
In terminal, 
1) Goto source directory 
2) Execute make command as root 
   make uninstall 
 
 
Copyright (c) 2008 Creative Technology Ltd. All rights reserved. 
==================================================================== 
  End of Readme File 
====================================================================

---

### Post by WannabeFantasma on 2010-03-15
There are other threads about this :)

I'm not sure what I did again to make it to work (I have an X-Fi card too)

I just found [http://www.overclock.net/sound-cards-computer-audio/409253-how-set-up-creative-sound-cards.html#post4868407](http://www.overclock.net/sound-cards-computer-audio/409253-how-set-up-creative-sound-cards.html#post4868407)
try that?
Hope it works so i can do that next time :D

---

### Post by ikt on 2010-03-15
> **robbiek01 said:**
> Hi All does anyone know how to install the creative XF-i drivers I'm not familiar with the command line and can't understand the creative instructions.

What version of ubuntu are you using?

From ubuntu 9.10 onwards Creative X-Fi sound cards work out of the box. (without installing any drivers.)

---

### Post by robbiek01 on 2010-03-15
im using 9.10 karmac but

---

### Post by 3rdalbum on 2010-03-15
The instructions you posted, and the HOWTO that WannabeFantasma linked to, are both from 2008. Ancient.

There have been two versions of Ubuntu and probably five new Linux kernels since then. I believe many X-Fi cards should be supported out-of-the-box in Ubuntu 9.10 using a better driver than what Creative has.

You've got no sound at all? What comes up if you right-click on the volume control applet and choose Sound Preferences, and go to the Output tab?

---

### Post by Perfect Storm on 2010-03-15
I know that XF-i XtremeGamer Fatal1ty Pro works out of the box (I got one). Which XF-I card do you have?

---

### Post by WannabeFantasma on 2010-03-15
Sorry about my ancient link... :) just searched a bit :) (might be the same? unzip - go into terminal etc?)

well I have a X-Fi xtreme gamer and it didn't work out of the box with ubuntu 

But I can't remember what I did :(

On other thread([http://ubuntuforums.org/showthread.php?t=1304627](http://ubuntuforums.org/showthread.php?t=1304627)) there was

> Your X-Fi should/may work on 9.10 after installing the

Code:
linux-backports-modules-alsa-karmic-generic

and rebooting.

---

