---
title: "wubi, boot flag"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by degarb on 2010-12-14
I can install wubi in c:, but on drive I:, no.

I wan't wubi on sde5.  I tried installing it with sde5 boot flag on and sde1 boot flag on. 

I like that the ntbtlrd comes up and offers me the two OSes.  I choose Ubuntu (grub), and just goes to a bash command line.  This when installing to.  

I really don't have enough free space to offer on c: 40 gig d: the 120 or the 200 gig internal drives.   I tried a 3 gig c: install, but Ubuntu ran out of room pratically during the install--on the updates.  So, this sucks.

<rant> There are several things about Linux I hate.  Among them the idiotic forcing of installed aps on main drive.  Like wearing a straight jacket, with no alternate clothing collection.  It is like buying large cloths for a child and naively thinking they will never grow out of them.   In windows, we can break our program or documents apart, filing them, as we choose.   I also think grub2 still has a long way to go, esp. to make Ubuntu work on external drives on older computers.</rant>

---

### Post by Hippytaff on 2010-12-14
You could do a 'real' install on a your I drive rather than wubi :-)

---

### Post by sanderd17 on 2010-12-14
What is your problem? you can create a separate partition for every folder in Linux.

The problem is that windows doesn't let you install wubi on I:. If you use separate partitions anyway, why stay with wubi? why not move to a dual boot?

---

### Post by degarb on 2010-12-14
I tried and failed at a real install.  Since installing grub to sde, didn't work. I don't know, and am asking, perhaps, if this was because I needed to boot flag the first (ntfs) partion of sde?

I installed grub on sde, but nothing happened. 
One expert here said installing grub on the primary master, would cause XP to not load if the external drive was unattached or failed.  So I avoided that option like the plague. (I want a companion to xp, not a killer.  Ubuntu has a ton of nice stuff, is easy once setup, and is fine for 80 percent of users.  But still, No voice recognition, working autohotkey, bbe sonic enhancer, and I can go on for hours. )

---

### Post by degarb on 2010-12-14
> **degarb said:**
> I tried and failed at a real install.  Since installing grub to sde, didn't work. I don't know, and am asking, perhaps, if this was because I needed to boot flag the first (ntfs) partion of sde?


However, the ntbldr didn't show ubuntu as an option.

The idea that installing grub in c: would replace the ntbtldr, and, if the linux drive were not present, even windows would not be accessible.....this is just insane!

---

### Post by lisati on 2010-12-14
> **degarb said:**
> However, the ntbldr didn't show ubuntu as an option.

The idea that installing grub in c: would replace the ntbtldr, and, if the linux drive were not present, even windows would not be accessible.....this is just insane!

If an installation of a dual-boot goes well, grub will include an option to boot from Windows. To expect any less would be insane. :)

---

### Post by degarb on 2010-12-14
> **lisati said:**
> If an installation of a dual-boot goes well, grub will include an option to boot from Windows. To expect any less would be insane. :)

In simple language of your own, elaborate.

The options I saw were: install grub in sde or install grub in sda.  sde did not work (but my boot flag wasn't on, but still did not show in windows boot menu, like wubi).   I avoided sda because I am told by expert here, that _this will cause windows to not be able to load if external drive is taken to work or swapped with another_. ***(Something, I was hoping would be disputed.  Yet, no one has disputed this.)***

---

### Post by degarb on 2010-12-14
Also, since there seems to be indications to me that installing grub to sda still will fail to load sde5 Ubuntu. (2002 bios machine, wubi didn't work on this partition) 

How would I get back the standard windows boot menu?  Or am I over thinking this?

---

### Post by degarb on 2010-12-14
xwubi available?

---

### Post by oldfred on 2010-12-14
Boot flag has nothing to do with wubi, other than wubi boots thru windows and windows boot partition has to have the boot flag. Wubi can be installed to other partitions, but has to be booted thru the windows install on sda.

Since you have an old IDE system you only have one MBR to boot from. If you want to create a small grub only partition on your boot drive, you could manually add a windows boot and then be able to boot Ubuntu installed elsewhere. It is a little more advanced but with your hardware restrictions, it is about all you can do.

Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)

---

### Post by degarb on 2010-12-14
> **oldfred said:**
> Boot flag has nothing to do with wubi, other than wubi boots thru windows and windows boot partition has to have the boot flag. Wubi can be installed to other partitions, but has to be booted thru the windows install on sda.

Since you have an old IDE system you only have one MBR to boot from. If you want to create a small grub only partition on your boot drive, you could manually add a windows boot and then be able to boot Ubuntu installed elsewhere. It is a little more advanced but with your hardware restrictions, it is about all you can do.

Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)

I take it you don't think the boot flag idea will help me with my real install.

[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)
this page is removed.

Making a partition of c: is no problem.  Then since you can only choose drive to install grub. I will read that thread on installing specifically into that partition.             

" manually add a windows boot "  no link for that.

---

### Post by degarb on 2010-12-14
Until I get this figured out.  I will install wubi. I see ubuntu 10 recommends 15 megs.  I installed 9 on a laptop with 600ghz and 6 gig hd.  A bit tight, but works great.

I might be able to sacrifice 8 gigs for a wubi install.   I really want a edubuntu (on I:  Downloading it now.)  So I will download many educational software I can afford.

---

