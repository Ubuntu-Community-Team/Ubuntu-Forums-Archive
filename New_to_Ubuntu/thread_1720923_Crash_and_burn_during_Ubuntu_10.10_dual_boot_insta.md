---
title: "Crash and burn during Ubuntu 10.10 dual boot install"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by BTragert on 2011-04-03
From Vista, I loaded the 10.10 iso file onto a USB stick, booted from it, and loved it.  I'd like to use it as my primary OS in a dual boot system.

I ran "Install Ubuntu 10.10" from the Ubuntu desktop, had a system crash trying to install alongside Windows.  Now when I restart (without the USB stick in), I get a 
"EDD:Error 04fd reading sector1401568
vesamenu.C32: not a Com32R image
boot:"

I can f10 during restart, and have the chance to run from USB again (that's what I'm doing now), but what now?  OEM Windows desktop PC with no Windows discs or a restore disk.

I downloaded the 10.10 iso file again (again using the USB to boot) and went to burn to a blank CD-R (thinking somehow I had a bad install file), and get a "not supported disc type" message.

Any thoughts would really be appreciated (as soon as the chuckling subsides).  Thanks.

---

### Post by Mark Phelps on 2011-04-04
Hard to give detailed advice without more information up front ...

When in Ubuntu, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out your partitions so we can see how your hard drive is configured.

Sorry to be the bringer of bad news, but if you allowed the Ubuntu installer to shrink Vista to make room for Ubuntu, there's a very strong possibility that Vista will no longer boot.  That process can result in corrupting the Vista OS partition, rendering it unbootable.

---

### Post by BTragert on 2011-04-07
Thanks, Mark!

Got it working through dumb luck and persistence -- probably have a few dozen partitions, but I'm sure loving the Ubuntu desktop environment.  Appreciate your help!

---

