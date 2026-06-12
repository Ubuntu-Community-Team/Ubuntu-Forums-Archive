---
title: "Can Ubuntu be installed without losing my current data?"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by SorinH on 2009-12-17
Now I'm using Windows 7 on my laptop, I want to remove it and install Ubuntu.Can this be done without losing my data?

Thank you.

---

### Post by northern lights on 2009-12-17
If your using a pre-installed Windows that came with a single-partition (i.e. "C:\") only, then you'd have to backup your data somehow (USB flashdrive, CD/DVD, external/second HDD).

If you've got more than one partition (i.e. "D:\"+), you can move your data there and install Ubuntu in the space previously occupied by Windows.

---

### Post by pmlxuser on 2009-12-17
shrink your windows parttion first, with some windows program like parttion maginc for example after that creat a new partion on which to install ubuntu. you could as well use the parttion editor that comes with ubuntu only that it requires specif care when installing. if your are good at following instruction then yeah you can do it... its possible indeed

---

### Post by 3rdalbum on 2009-12-17
> **SorinH said:**
> Now I'm using Windows 7 on my laptop, I want to remove it and install Ubuntu.Can this be done without losing my data?

Your data is most probably stored on the same partition as Windows 7, so no. You need to back up all your data before installing Ubuntu. It reformats your disk.

---

### Post by 3rdalbum on 2009-12-17
> **pmlxuser said:**
> shrink your windows parttion first, with some windows program like parttion maginc for example after that creat a new partion on which to install ubuntu. you could as well use the parttion editor that comes with ubuntu only that it requires specif care when installing. if your are good at following instruction then yeah you can do it... its possible indeed

This advice would be fine if the OP wanted to dual-boot, but according to the post they want to remove Windows 7.

---

### Post by Hetepeperfan on 2009-12-17
Alternatively you can use a Live cd. First try Ubuntu without making any changes. So you can figure out if you like Ubuntu without making any changes to your current system.

Best,

Maarten

---

### Post by Aaron2694 on 2009-12-17
The first option is to use an Ubuntu Live CD and mount your hard drive. Back up what you need with the Ubuntu One Cloud storage space.  If you dont want to do that then your next option is to use an Ubuntu Live CD and mount your hard drive and any external storage device and copy your files onto the external storage.

---

### Post by PriceChild on 2009-12-17
Last I checked, the Ubuntu installer **does not** format your disks or partitions unless you tell it to. You will be able to resize the win7 partition then copy anything you want over.

What you can not do, is install Ubuntu on your existing win7 partition. Ubuntu won't boot off of an ntfs partition. You will need to have an ext (or other choices) partition to install on.

Ubuntu would be able to read whatever ntfs partitions you have though.

Before you do anything... **Backup all data on your drive that you want to keep. **Mistakes and bugs happen.

---

### Post by PriceChild on 2009-12-17
> **Hetepeperfan said:**
> Alternatively you can use a Live cd. First try Ubuntu without making any changes. So you can figure out if you like Ubuntu without making any changes to your current system.

Best,

MaartenThat's also a great suggestion.

---

### Post by northern lights on 2009-12-17
> **Aaron2694 said:**
> The first option is to use an Ubuntu Live CD and mount your hard drive. Back up what you need with the Ubuntu One Cloud storage space.
If your into having online data, have a decent broadband connection and less than 2GB overall to backup - then, fair enough, this might be a viable option.

> **Aaron2694 said:**
> If you dont want to do that then your next option is to use an Ubuntu Live CD and mount your hard drive and any external storage device and copy your files onto the external storage.
Why in the world would the OP not just connect that very external storage device to his existing Win7 installation???

Please don't make things sound more complicated than they are. Thank you.

---

### Post by Aaron2694 on 2009-12-17
> **northern lights said:**
> If your into having online data, have a decent broadband connection and less than 2GB overall to backup - then, fair enough, this might be a viable option.
 
 
Why in the world would the OP not just connect that very external storage device to his existing Win7 installation???
 
Please don't make things sound more complicated than they are. Thank you.
 
I guess you are right. *bows*

---

### Post by mikechant on 2009-12-17
Personally what I'd do is the following:
[LIST=1]
[*]Use Windows 7's own utilities to defragment the disc
[*]Use Windows 7's own utilities to shrink the windows partition as much as it will allow**
[*]Install Ubuntu into the free space (default)
[*]Copy any data you want to keep from the windows partition into the relevant Ubuntu partition/s
[*]You now have a dual boot system and can start using Ubuntu seriously.
[*]When you're sure you don't want Windows anymore use gparted in Ubuntu to delete the windows partition
[*]finally use gparted to resize the Ubuntu partition/s to use the space freed by deleting windows
[/LIST]

**It's always best to use Windows's own utilities to shrink Windows partitions.

Doing it this way means you can go back to Windows without reinstalling if you don't get along with Ubuntu, or you can keep the dual boot setup if you find there's an odd thing or two you can't do in Ubuntu (eg in my case I kept a Windows install purely to run the special reformat routine for my mp3 player, which wouldn't run in Linux and needed to be run if the player got corrupted).

You should still backup any important data before doing any partition related operations.

---

### Post by chuina on 2009-12-17
Hey , **SorinH**,

I think u should tell your Hard Disk Partition info first.
Like number of drives C,D,E.....Their size...
Which partitions data u want to save ?

Then the solution for your installation is only a step away in this forum:P!!!









-----------------------
i love this forum
-----------------------

---

### Post by SorinH on 2009-12-17
I have a 320Gb hard disk with four partitions. On C:\ I have Windows, my data are on other partitions. So it is save to try to install Ubuntu?

---

### Post by northern lights on 2009-12-17
For a first time *nix user, it might be a good idea to just resize one or the other partition and dual-boot both systems for a bit.

If you're already certain you want to completely dump Windows, it is safe to install Ubuntu instead, technically speaking.

However, watch out when installing: Do not choose "Guided Partitioning", since that will wipe the entire disk. Instead choose "Manual installation". If you're familiar with partitioning under Windows you should be able to deal with that.

Are you aware of having to have a swap partition (virtual memory, pagefile equivalent)?
Further, I'd advocate a separate /home, but that's not quite as important as you have further data partitions.

---

### Post by oldfred on 2009-12-17
If you already have 4 partitions you may have issues. You can have 4 primary partitions or 3 primary and one extended that can contain many additional logical partitions. Ubuntu can be installed in logical partitions but if you have used all 4 primary, you will have to delete one partition to allow for an extended partition. Much resizing and moving of partitions will also be required.

---

### Post by chuina on 2009-12-17
Also make sure that u can connect to the Internet by booting 
from your Live CD.
Because sometime net connectivity need extra steps which 
by default can't be done.
i have this experience, so i'm just reminding u.

---

### Post by SorinH on 2009-12-20
I have installed Ubuntu successfully and all my data is intact.Thank you guys for your suggestions.

---

