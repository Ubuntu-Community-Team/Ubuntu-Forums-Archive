---
title: "Questions Before I Download"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Cullent92 on 2009-12-28
I just received an old Toshiba Satellite laptop with Windows Vista Home Premium on it. I want to experiment with the Ubuntu operating system and want to know if I install it, will it completely erase Windows or not allow me to return to windows?

---

### Post by MelDJ on 2009-12-28
you can choose to install it through a few ways:
1. erase the whole disk and windows
2. make a partition for ubuntu, preserving windows and letting you choose which to boot into at startup
3. install through wubi to make ubuntu an application inside windows and you can choose which to boot from at startup

you can also just burn ubuntu to a live cd adn boot from it to try the live cd mode

---

### Post by Cullent92 on 2009-12-28
How do I make a partition? And if I do, how do I erase Windows if I decide to just use Ubuntu?

---

### Post by MelDJ on 2009-12-28
see this [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by PsychoDevon on 2009-12-28
WHENEVER you are scared of Ubuntu, I always recommend using Wubi. Just install Wubi like any other application from [http://wubi-installer.org/]("http://wubi-installer.org/") , and read EVERYTHING from there, it explains everything I possibly could and more.

---

### Post by 3rdalbum on 2009-12-28
> **Cullent92 said:**
> How do I make a partition? And if I do, how do I erase Windows if I decide to just use Ubuntu?

There is a screen in the installer where it gives you the options to:

o Erase Entire Disk
o Resize partition and make space for Ubuntu *(this is what you use for dual-boot)*
o Set up partitions manually *(you probably don't want this)*

When you select the Resize Partition one, you are presented with a bar graph at the bottom of the window. There is a slider towards the right of the graph. Grab this and drag it towards the left to shrink the Windows partition. You can see how much space will be allocated to Windows and how much to Ubuntu.

When you're satisfied, click Next and you'll be asked to confirm your changes. Click Next again and the partition resizing will be done.

I highly recommend defragmenting your hard disk from within Windows before installing Ubuntu. Ubuntu does defragment your disk to an extent to make space, but the Windows defragger will be quicker and more effective.

---

