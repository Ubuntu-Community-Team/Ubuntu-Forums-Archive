---
title: "Can't boot! Grub loading error 22."
date: 2009-07-30
forum: New to Ubuntu
---

### Post by Coh3n on 2009-07-30
Hey guys, so I deleted my Ubuntu partitions because I never used it and I needed to space for Windows.  So after I did the partitioning I get:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22

I don't understand how that happens considering there's no Ubuntu on my system anymore.  I've tried booting from my Vista Live CD and doing Startup Fix and that didn't work.

Please help me, I'm willing to reinstall Vista if I have to, but there are several files I need to backup first.  If there is a way to boot in Safe Mode or something please tell me.

Thanks.

---

### Post by nhasian on 2009-07-30
no worries, just boot off your vista disc and select the option to repair the bootloader.  then you will be able to boot back into vista.

also this link might help:

[http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/](http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/)

if you dont have the vista CD handy, you can still fix your mbr with the supergrubdisk

---

### Post by Coh3n on 2009-07-30
> **nhasian said:**
> no worries, just boot off your vista disc and select the option to repair the bootloader.  then you will be able to boot back into vista.


That's what I mean I've done that and the error still comes up, when I went to do it the second time it said there was nothing wrong with my start up.

---

### Post by nhasian on 2009-07-30
did you try the instructions from the link?  booting from the vista cd to a command prompt and running the fixmbr tool?

---

### Post by Coh3n on 2009-07-30
> **nhasian said:**
> did you try the instructions from the link?  booting from the vista cd to a command prompt and running the fixmbr tool?

I love you! <3

Thanks so much. :D

---

