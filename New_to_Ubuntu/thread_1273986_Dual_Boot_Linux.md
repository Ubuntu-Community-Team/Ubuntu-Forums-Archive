---
title: "Dual Boot Linux???"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by kfitzenreiter on 2009-09-24
Hello everyone.
First, I wanted to thank everyone for their replies to my posts in these forums.  I'm new to the "ubuntu forum" website and I appreciate any and all linux wisdom that is shared with me.
 
I enjoyed my recent Jackalope installation so well I'm installing it on another pc I have as I type.  Not to go on and on, but I sort of collect old computers from friends, coworkers, etc.  I even have a lady that collects metal from dumpsters (yeah, a dumpster diver LOL) and if she finds an old hp, dell, whitebox, etc she'll throw it into the back of her truck and see if I want it.  You'd be surprised how much good hardware minus a bad hard disk that is waiting for the garbage collector.
 
Anyway, my question this time is this?  How would one go about dual booting ubuntu with mandriva?  I have tried mandriva spring 2009 and I find it is quite good also and I would very much like to dual boot the two OS's...

---

### Post by renkinjutsu on 2009-09-24
You can just install mandriva on another partition. I've never installed mandriva, so i don't know the installation proccess, but i'm sure there's a partition utility. If you shrink your ubuntu partition, you'll be able to install mandriva on the free space..

as for getting mandriva to boot; The installer would probably install a bootloader for mandriva, this will overwrite grub and you won't be able to boot into ubuntu anymore.
But to fix this, pop an ubuntu liveCD and head to terminal and type ```
sudo grub
```
then ```
find /boot/grub/stage1
```
then set, your root to whatever the previous command gave ```
root (hdx,y)
```
then do 
```
setup (hd0) or whatever number 'sposed to go there
```

Now you have grub loading again to boot up ubuntu!!

now to edit your menu.lst file! Boot into ubuntu and ```
gksu gedit /boot/grub/menu.lst
```

scroll to the bottom and add an entry like:
```
title Mandriva
root (hdx,y)
chainloader +1
```

as for (hdx,y) in your menu.lst, you can find that out with
```
sudo fdisk -l
```
This should give you a series of /dev/sda's
determine which one Mandriva is installed on

and the partition number listed from fdisk is 1 more than what grub interprets (because Grub starts reading from 0)
so for example, if your mandriva is installed on
```
/dev/sda8
```
then what you put as root in your menu.lst would be
```
root (hd0,7)
```

---

### Post by grahams on 2009-09-24
Create 4 partitions on a hard drive with a tool like fdisk, gparted etc. 

1 for swap (common to both OSes) - size depends on ram size 
1 for ubuntu - 6GB or higher (depending on usage)
1 for Mandriva - 6GB or higher (depending on usage)
1 for /home (can be common to both OSes) - depends your usage and disk size (typically I pick what ever is left)

Note. choose a file system for /home that both OSes can use i.e. don't pick ext4 unless both can support

---

### Post by Michael.Godawski on 2009-09-24
Moved to ABT. ;)

---

### Post by andrew.46 on 2009-09-24
Hi kfitzenreiter,

> **kfitzenreiter said:**
>  How would one go about dual booting ubuntu with mandriva?

I wonder if rather than going to the hassle of partitioning you would consider the use of a Virtual Machine using software such as VirtualBox? There is a special section of these forums devoted to this subject:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

I attach a screenshot of VirtualBox in action on my own system :).

Andrew

---

### Post by kfitzenreiter on 2009-09-24
Thanks for your reply.
 
Seeing your picture made me smile because I recently achieved XP running on Ubuntu in Vbox for the first time two nights ago.  It may sound silly, but I've been trying to get that to work for quite a while now and I finally did.
 
As for using it for mandriva, I guess one reason I want to do a "real" install vs. a vbox version is I want to learn more about configuring the boot process in Linux.  Kind of like when I learned more about the "boot.ini" file in Windows xp/windows 2000 etc.  I also want to learn how to fix a hosed boot process on a linux install, be it mandriva or ubuntu or whatever.

---

### Post by Darkwing-Duck on 2009-09-24
Another way to get GRUB to boot both at once... Try this guide it may help you.
 
[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by kfitzenreiter on 2009-09-26
Well, I already bookmarked your "reinstall grub" advice since that is what I wish to learn.  The "sad" thing is when I installed ubuntu over the top of my Vista/Mandriva installation, ubuntu handled the whole thing itself.  In other words, it configured a triple boot system without any help form me.
 
Now grub offers up a choice of ubuntu, mandriva, or vista upon booting up.  Pretty neat, if I say so myself.  I don't know how long the competing linuxes (is that a word) will last since ubuntu installed itself "next to" mandriva on the same partition.  The good news is there is currently nothing of any great importance on the laptop.
 
Thanks to all.

---

