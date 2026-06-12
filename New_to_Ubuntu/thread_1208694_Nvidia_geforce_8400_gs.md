---
title: "Nvidia geforce 8400 gs"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by A' Podartho on 2009-07-09
I know other threads are dealing with sundry nvidia graphics card issues.

BUT, the versions are different from what I have. what should I do ? 
I'm a bit jittery by the problems people are facing. please advice.

---

### Post by CLomax on 2009-07-09
If you're referring to the installation of drivers...

The first port to call is checking **System -> Administration -> Hardware Drivers** for a proprietary driver.

Failing that: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Troll_the_Great on 2009-07-09
> **A' Podartho said:**
> I know other threads are dealing with sundry nvidia graphics card issues.

BUT, the versions are different from what I have. what should I do ? 
I'm a bit jittery by the problems people are facing. please advice.

First, can you tell us what exactly is the problem? Your system specs and version of Ubuntu will also help.
Cheers!

---

### Post by A' Podartho on 2009-07-10
system specs : AMD Phenom X3, 2 GB RAM, Ubuntu 9.04.

dual boot with XP.

T TG, no problem so far since I haven't tried anything. discussions in other threads say some people ended up up with blank screens while trying to install drivers.

I don't want to do end up with that !

also, which one should I install, 173 or 180 ?
thanks in advance.

---

### Post by Arup on 2009-07-10
I have installed drivers via Jockey hardware applet or through the sh downloaded from nvidia site, never have faced problems. For installing via nvidia sh, make sure to completely purge linux restricted modules and older nvidia drivers in case they were installed and I guarantee you that you won't get any blank screens.

---

### Post by A' Podartho on 2009-07-10
> **Arup said:**
> I have installed drivers via Jockey hardware applet or through the sh downloaded from nvidia site, never have faced problems. For installing via nvidia sh, make sure to completely purge linux restricted modules and older nvidia drivers in case they were installed and I guarantee you that you won't get any blank screens.
could I have a bit more detailed instructions regarding installation ??
what exactly do I have to do ?

my only experience with linux was in an environment where users had no installation privileges whatsoever.

sorry for being such a n00b !

---

### Post by 3rdalbum on 2009-07-10
I've installed drivers for an Nvidia 8600 GT (same era as your card) without problems at all. Complete video-loss problems are actually very rare these days, and most of the time they only happen to people who have very old Nvidia cards.

Chances are that you've already worked out how to install the driver; if you haven't, then you just go to System > Administration > Hardware Drivers. The program will offer you the correct driver, all you need to do is hit Activate.

---

### Post by Mornedhel on 2009-07-10
I have an NVidia GeForce 8400M GS. Works fine with the 180 driver. It used to segfault about once a week in random circumstances, but it hasn't since the last update.

You can get a list of video cards supported by the 180 driver with

```
apt-cache show nvidia-glx-180
```

---

### Post by A' Podartho on 2009-07-10
> **3rdalbum said:**
> I've installed drivers for an Nvidia 8600 GT (same era as your card) without problems at all. Complete video-loss problems are actually very rare these days, and most of the time they only happen to people who have very old Nvidia cards.

Chances are that you've already worked out how to install the driver; if you haven't, then you just go to System > Administration > Hardware Drivers. The program will offer you the correct driver, all you need to do is hit Activate.
you guessed right, I did install ver 180.

thanks everyone who replied !
[B]
But there is still a problem with settings I think. how do I check my settings and adjust it ?[/B]
or should I start a new thread ?

currently the pages aren't looking too good, the smilies for example are looking simply horrible.

---

### Post by Troll_the_Great on 2009-07-10
> **A' Podartho said:**
> you guessed right, I did install ver 180.

thanks everyone who replied !
[B]
But there is still a problem with settings I think. how do I check my settings and adjust it ?[/B]
or should I start a new thread ?

currently the pages aren't looking too good, the smilies for example are looking simply horrible.

If you are referring to the video settings, you can change them using the Nvidia Settings that was automatically installed with your video driver. You can find it under System - Administration - NVIDIA X Server Settings.
Cheers!

---

