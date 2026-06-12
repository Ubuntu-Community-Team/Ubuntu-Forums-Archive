---
title: "GRUB problems with triple boot"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by steve228 on 2009-10-24
Hello all.

I am planning on adding Windows 7 to my dual-boot (Windows XP, Ubuntu 9.04) machine.  What will this do to the GRUB menu?

I remember a situation I had like this before and neither GRUB nor my actual Windows installation would load... i can't remember the error, but I think it was an error involving loading the GRUB.

Has anyone had success installing Windows after Ubuntu?  
How can I keep the GRUB loader default when installing W7?

**Thanks in advance for your replies**


*P.S Don't worry, Ubuntu will still be my regular lol.*

---

### Post by jrrader on 2009-10-24
Windows 7 does not want you using XP or Ubuntu.  You will have to rescue your Ubuntu with super grub disk.
[URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"]
Here is a complete guide to rescuing Ubuntu[/URL]

After your grub is back, you can add entries for XP and 7 by following the instructions inside /boot/grub/menu.lst

---

### Post by Sylslay on 2009-10-24
I had replace XP with win7 beta  and than install grub from livecd. all in one evening ... sukcess

If you do clean install:
xp - first , win7 -second, than ubuntu should be 3 boot at grub

but 
isntalled gentoo + ubuntu + fedora = big mess and huge Delete
waist of time and .....no sukcess

---

### Post by Mark Phelps on 2009-10-24
> **steve228 said:**
> Hello all.

I am planning on adding Windows 7 to my dual-boot (Windows XP, Ubuntu 9.04) machine.  What will this do to the GRUB menu?[/I]

Installing Windows 7 will not do ANYTHING to the GRUB menu.  That is inside an Ubuntu installation which Windows 7 can not read.

What it WILL do is two things:
1) Overwrite GRUB in the MBR.  You were provided a link to restoring this.
2) Create the Windows 7 bootloader files in the existing XP partition.

What this means is, when you're done, the MS Windows entry in menu.lst will only allow you to boot into a MS-provided OS options menu.  You will than have to choose which OS you want to use -- XP or 7.  That's simply the way it works.

---

### Post by jrrader on 2009-10-24
> **Sylslay said:**
> 
but 
isntalled gentoo + ubuntu + fedora = big mess and huge Delete
waist of time and .....no sukcess

I have several different linux distributions on my home computer (I'm on my laptop at school right now so I can't show you my actual grub).  There is a trick to it and it took a long time to get it right.  On my HDD I have 5 partitions near the front, all about 500MB each, for boot partitions.  I installed Ubuntu first so I let the master boot record go to sda.  For the others, I put the master boot record in their own boot partitions (usually you specify this by clicking an "advance" button right before install).    After Fedora is installed, go into Ubuntu and edit /boot/grub/menu.lst so you have a line like this:

```
title   Fedora 11
configfile   (hd0,1)/grub/grub.conf #(hd0,1) is sda2
chainloader +1
``` 

With the proper hd location (/boot is left off because (hd0,1) is /boot).

If grub.conf does not exist, this will work:
```
title     crunchbang linux
root (hd0,2) #(hd0,2) is sda3
chainloader +1
```

When you turn on your computer the Ubuntu grub will load.  If you select Fedora 11 or crunchbang, rather than booting directly into them, their own grubs will load.  Of course you can edit their menu.lst so timeout is 0 and it appears as if grub is being skipped.

(I will check my menu.lst when I get home to make sure this is actually how I got it working)

---

### Post by jnorthr on 2009-10-24
why would anyone in their right mind want to use windows ????????????

been taking one too many tablets there sport  :KS

---

### Post by swerdna on 2009-10-24
> **jnorthr said:**
> why would anyone in their right mind want to use windows ????????????

been taking one too many tablets there sport  :KS

Because I get paid to use it and my kdz need to be educated

---

### Post by Mauler5858 on 2009-10-24
Another way to accomplish this would be to:

1. Remove the current hard drive.

2. Put in a fresh one and install Win 7 on it.

3. Put the other hard drive back in and configure your grub to recognize the Win7 installation.

The advantage to this is that for redundancy, if your main hard drive crashes...you can always immediately boot to the win7 hard drive by itself until you have time to rebuild.

---

### Post by Sylslay on 2009-10-24
use windows for upgrade mp3, mobile phones, cameras

and still for skype ..... 
skype dont work ok since ubuntu 8.04 :-(
:(:confused:

ps
 Great idea, Mauler5858
 if have 2 hdd, than press f12 and boot direct and can configure grub on first hdd. too

---

### Post by carnagex420x on 2009-10-24
you can just boot from a LIVE Cd and reinstall GRUB w/o reinstalling the OS which is way easier. Then add the windows option to your menu.list.

```
grub
find /boot/grub/stage1 #tells you where grub is
root (hd0,x)
setup (hd0,x) #to install to a partition
or
setup (hd0) #to install to the MBR
quit
```

menu.list

title Windoze
root (hd0,x)
chainloader +1

---

