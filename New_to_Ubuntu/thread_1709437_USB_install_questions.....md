---
title: "USB install questions...."
date: 2011-03-18
forum: New to Ubuntu
---

### Post by CVGH on 2011-03-18
Hi!

I booted Ubuntu 10.10 32bit from CD and then ran the "make start-up disk" using a 16GB USB flash drive.

1) Why only a 4GB persistence? Like to use more if possible...
2) Any way to stop the Welcome message asking to run or install?


Thanks!

Brian

---

### Post by andrewthomas on 2011-03-18
> **CVGH said:**
> Hi!

I booted Ubuntu 10.10 32bit from CD and then ran the "make start-up disk" using a 16GB USB flash drive.

1) Why only a 4GB persistence? Like to use more if possible...
Brian
You probably need more than one partition.
> **CVGH said:**
> 
2) Any way to stop the Welcome message asking to run or install?

Have you read this?
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by CVGH on 2011-03-18
> **andrewthomas said:**
> You probably need more than one partition.

Have you read this?
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I have now! Thanks Andrew!!

---

### Post by ameanjoe on 2011-03-18
Some time ago I installed a 500GB external Drive on my desktop,
connected via USB, then installed Ubuntu 10.04 on it. Now I want to remove it (and Ubuntu which I never use). I don't remember how I did the install, or if it was automatic, and I don't know how to remove it cleanly. When I boot my computer I am offered a selection of versions of Ubuntu, with Win Media Center stuck in the middle. I have to quickly select it (that's what I usually use). Sometimes it will just come up with a GRUB error and I don't know how to get past that. I would just like to get rid of the Ubuntu and be able to use the external drive for back-ups.
If any of this makes any sense to anyone who can help me I would be deeply appreciative.

---

### Post by I2k4 on 2011-03-18
This is interesting to me, because I've been running Lubuntu off a 4GB USB with 2GB for the OS and 2GB for Persistence (storing all my images, videos, etc. on the HDD.)  

I really haven't noticed the need for huge "Persistence" and would only expect to need lots of space for additional packages if I installed a lot more packages.  As it is, I've used less than 1GB in the Lubuntu space, but have no idea how much is being used of the Casper / Persistence file.

Is there something informative about how much actual drive space "Persistence" uses?  I've been thinking it might just be to save settings and preferences, and might be much less than the 2GB I've given it.

---

### Post by CVGH on 2011-03-20
I'm used to windoze bloat I guess, so I wanted as much space as possible. LMMS took 250MB for instance...
I'm thinking I might shrink casper-rw down a few gigs and make a FAT32 partition to share files when I plug it into window$e.
Hopefully it won't break something....

---

