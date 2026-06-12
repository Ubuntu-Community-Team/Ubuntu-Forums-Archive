---
title: "ati driver not installing or not working"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by I8NY on 2009-08-10
So i have Ubuntu 64bit and i can't get the ati driver working.  I have tried open source and the ati web site driver multiple times and they do not work.  The fglrx driver would install fine but when ever i ran a openGL app, xorg would hog up %100 cpu.(or when the pc was idle)   And the app had low fps when they should be a lot higher.  I have tried turing on the restricted drivers and gotten them on but i had the same problem.  The [open source driver]("https://help.ubuntu.com/community/RadeonDriver") installed but then ubuntu wouldn't start with the xorg.conf settings and i would have to restore them to the old file.  And with the open source driver once i did boot back into ubuntu i couldn't run my openGL app.  I have reinstalled ubuntu 3 or 4 times now trying to get the driver working.  I have a clean install of ubuntu now to work with.

spec: AMD 720 x3 cpu
XFX Radeon HD 4850 512MB
2gb ram
1tb hdd

---

### Post by phillw on 2009-08-10
Hi,

I've had a good trawl round for you ....   The best I can up with is a site where they're discussing your card family & a couple of the experienced guys on there are running 64 bit & ubuntu ... They may be better placed to help. There is a similar request in the media forum on ubuntu - so, I'd give this link a try.

Hope it is of help.

[http://www.techsupportforum.com/hardware-support/video-card-support/397502-xfx-radeon-hd-4870-my-build.html](http://www.techsupportforum.com/hardware-support/video-card-support/397502-xfx-radeon-hd-4870-my-build.html)

Regards,

Phill.

---

### Post by I8NY on 2009-11-17
Ati didn't support ubuntu 9.04 yet but there new driver does

---

### Post by Mark Phelps on 2009-11-18
> **I8NY said:**
> Ati didn't support ubuntu 9.04 yet but there new driver does

What???

ATI DOES support 9.04, just only for the newer HD 3x/4x/5x cards and the equivalent Mobility Radeon cards.

It does NOT support the old "legacy" cards, neither in 9.04 nor in 9.10.

Apart from rumoured problems with the Catalyst 9.10 drivers, AFAIK, ATI support in 9.10 is no different than it was in 9.04.

---

### Post by emigrant on 2009-11-18
hi all,
how can i see whether i have installed ATI drivers?

---

### Post by I8NY on 2009-11-19
Yes ati does support ubuntu 9.04 and 9.10 but i was trying a old driver so it wouldn't work.

emigrant, to tell if you have the ati driver installed go to System>Administration>Hardware Drivers.  There will be a ati driver listed there and if it is installed there will be a green circle by it.

---

