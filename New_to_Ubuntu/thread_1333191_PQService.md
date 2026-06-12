---
title: "PQService"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by welshhelen on 2009-11-21
Hello.

I've been running Ubuntu for around 6 months now after my Windows died and a kind friend directed me towards Ubuntu and installed it for me making the machine ostensibly dual boot.

I want to continue to use Ubuntu, I love it and have no desire whatsoever to return to Windows.

However it seems that that I am going to need to repair my Windows partition and make it bootable for work stuff.  There is proprietary software that we use that will only work on Windows.  I can't make it run on Ubuntu and it doesn't run through Wine.

The reason I didn't didn't just repair the Windows installation is because the recovery discs I had made had fallen out of their box and were really scratched up.

But I do still have the PQService partition.  Does anyone know how I can use that to repair my Windows?  Either to directly use it to repair without damaging my Ubuntu installation or to create a disc which I can boot from and will then repair the Windows installation.

I know it seems strange to ask about Windows on an Ubuntu forum but everywhere I've looked talks about having to take out GRUB or things that will make me not able to boot into Ubuntu.

I want to continue to use Ubuntu but to be able to boot into Windows when I have to do some work stuff at home.

I'm currently running Jaunty but will be upgrading to Karmic as soon as I've got time.

Thank you.

---

### Post by fromthehill on 2009-11-21
if your windows partition is still there you can do this
[http://ubuntuforums.org/showpost.php?p=8359589&postcount=9](http://ubuntuforums.org/showpost.php?p=8359589&postcount=9)

if you don't have windows installed you can install it on a empty partition. you will be able to boot into windows after that

if you can boot in windows follow these steps
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

I wouldn't use the pq partition
the recovery menu's i've seen arent that advanced.
since almost every laptop by default has two partitions it will probably only give you the choice of wiping you first partition(which on default had windows on it) or wiping the first two partitions.

---

### Post by welshhelen on 2009-11-21
Thank you.  I do have Windows installed on one partition.  I can access all the files that are on there through Ubuntu but I need to be able to boot into Windows sometimes.

Windows was fine then one day it would seem a file corrupted or something so that it wouldn't boot into it.  At which point a friend put on Ubuntu on a different partition leaving the Windows one intact so that it could be repaired at some point.

I have several partitions, Windows, Ubuntu, sharedspace, PQService and a swap.

I don't have the recovery disc because it is scratched up too much to use, which is needed for your first point, which is why I have a problem.  I know the recovery disc was made from the PQService partition.  Would it be possible to make a new recovery disc from that?

---

