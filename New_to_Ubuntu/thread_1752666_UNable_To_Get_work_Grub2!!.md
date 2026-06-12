---
title: "UNable To Get work Grub2!!"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Arifcatalyst on 2011-05-08
I installed Ubuntu v10.10 From Wubi!!!

I Replaced Grub Wid Geub2 aka Burg(found ON OMG Ubuntu) [http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/](http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/)

BUt What I Get Z this Sh*t... :popcorn:[IMG]http://i53.tinypic.com/9awzg6.jpg[/IMG]






I Repaired MY bootloader Through Windows7 Cd Numerous Times!!!
Reapairing My bootlloader Dena Again Checking IF This Worked!!! Den again Repairing!!!
It has become My Nightmare!!

SOMEdbody Genius Drag ME OUT oF  This JAM!!!!!!!!!!!   :confused:

---

### Post by powerpleb on 2011-05-08
Ugh! I hate this sort of thing.

Grab a live CD and follow these instructions: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

And for future reference, messing around with theming the boot loader is definitely not worth the risk IMHO.

---

### Post by Arifcatalyst on 2011-05-08
> **powerpleb said:**
> Ugh! I hate this sort of thing.

Grab a live CD and follow these instructions: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

And for future reference, messing around with theming the boot loader is definitely not worth the risk IMHO.
AH!!! thanxxx man.....dO U Know HOw To Install Ubuntu In a diff partition!

I tried Once....Installing directly on whole disk...but its Eat Too Much space...i meant that One partiiion for Installing(its OK) BUt wtf??? another whole artition For swap!!!:confused:

---

### Post by Not unique on 2011-05-08
Try these to help with dual booting and partitioning:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

Hope they help some.

---

### Post by Arifcatalyst on 2011-05-08
> **Not unique said:**
> Try these to help with dual booting and partitioning:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

Hope they help some.

BUt I say What.... These All R written al;ike AS IF I know Everything!!!! Just BRowsing IF im correcT O r not???

---

### Post by Rubi1200 on 2011-05-08
If you installed with Wubi you **cannot **use boot managers like Burg or install GRUB to the MBR.

That error is the result of what you tried to do.

You need to leave the Windows bootloader alone and let it control the boot process.

You will then have the menu where you can choose between Windows and Ubuntu.

Also, don't change the default timeout for Windows as this can also cause problems.

---

### Post by Not unique on 2011-05-08
Edit:-  Yes in future install Ubuntu AFTER Windows but NOT with Wubi maybe.

How about these two then:

[http://seogadget.co.uk/the-ubuntu-installation-guide/](http://seogadget.co.uk/the-ubuntu-installation-guide/)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Or just type something like " Ubuntu seperate partition install made simple easy  " into Google.

---

### Post by Arifcatalyst on 2011-05-08
> **Not unique said:**
> Edit:-  Yes in future install Ubuntu AFTER Windows but NOT with Wubi maybe.

How about these two then:

[http://seogadget.co.uk/the-ubuntu-installation-guide/](http://seogadget.co.uk/the-ubuntu-installation-guide/)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Or just type something like " Ubuntu seperate partition install made simple easy  " into Google.

DUDE!!! Thanxxx A lOt 

BUt what Bout GRub2!!! will it work Wid Wubi!!! ANd yeah I wanted My Windows Bootloader To Be deleted In the situation That I cud REcover It later??

How to Do that?? :P

---

### Post by Not unique on 2011-05-08
This is a little bit above me so you could wait for other advice or for me I would back up and format then install Win then Ubu NOT via Wubi or Wubu or whatever the hell it is that works great for me. And that way Ubuntu sorts everything i.e. the Win **M**aster-**B**oot-**R**ecord and then best to leave them to do there own thing..

I learn't the hard way not mess about with things too much but on the other hand that is how I learn't things but I had to repair and REinstall my OS's MANY times.

---

### Post by Arifcatalyst on 2011-05-08
HEll!!! teah....can any give Me  A TUt how to TRansform Wubi into THe freshly Baked Ubuntu On separate Partiiton!!!!!

I have done Heck Lot of it in It!!! so i dont wanna go In all those stufff Of reinstalling and customising Into MY demands!!!:P

---

### Post by Rubi1200 on 2011-05-08
I repeat what I said before, you _**cannot**_ use GRUB or GRUB2 or a boot manager to boot a Wubi install.

If you have a Wubi install that you have customized and would like to migrate it to a partition that you prepared on the drive, here is the best guide I know of:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

If you have any specific questions about this, ask in that thread and I am sure bcbc will be more than happy to help.

---

### Post by Not unique on 2011-05-08
Best listen to Rubi1200 some one who's drunk that much coffee more than likely knows his stuff.
It certainly sounds that way.

Reinstalling's not such a big deal just backup and re-do it won't take long, besides it's nice to have a fresh and clean working install to start from scratch sometimes.

---

