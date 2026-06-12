---
title: "where is gparted ?"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by jrev on 2009-10-08
Hi all,

I am wondering where is gparted which was a good help in the previous versions to know how full were your partitions or your hard disks.
I cannot see it on ubuntu 9.04

What is worse is that there is no such tool on the eeebuntu's version.
I have an Asus 701 4G and my hard disk is almost full.

How can I use the 8 Go SD card to share the OS (and data) between them ?

Thanks for a good answer :P

---

### Post by Mark Phelps on 2009-10-08
Gparted is not installed by default in Ubuntu; however, it shows up automatically on the LiveCDs.

Recommend using Synaptic to download and install it.

---

### Post by snowpine on 2009-10-08
In the Ubuntu repositories.

```
sudo apt-get install gparted
```

Then, it should appear under System-Administration-Partition Editor.

---

### Post by swoody on 2009-10-08
Please note that Ubuntu does come with Disk Usage Analyser which can be found under Applications>Accessories>Disk Usge Analyser. It is safer than gparted, as some people may not be aware that gparted can really mess up your computer if you do not know what you're doing with the program.

---

### Post by philinux on 2009-10-08
> **jrev said:**
> Hi all,

I am wondering where is gparted which was a good help in the previous versions to know how full were your partitions or your hard disks.
I cannot see it on ubuntu 9.04

What is worse is that there is no such tool on the eeebuntu's version.
I have an Asus 701 4G and my hard disk is full.

How can I use the 8 Go SD card to share the OS (and data) between them ?

Thanks for a good answer :P

+1 all the above.

Also try this.

```
df -h
```

---

### Post by CharlesA on 2009-10-08
> **swoody said:**
> Please note that Ubuntu does come with Disk Usage Analyser which can be found under Applications>Accessories>Disk Usge Analyser. It is safer than gparted, as some people may not be aware that gparted can really mess up your computer if you do not know what you're doing with the program.

I bumped into that program while poking around, quite handy. :D

+1 to everyone else, gparted is very dangerous since it can delete and create partitons, as well as show how much disk space is left.

Disk Usage Analyzer is the safer way to find that info.

---

### Post by oldfred on 2009-10-08
It makes sense that gparted is not normally installed as you cannot run it from anything that is mounted. If you have a second drive you possibly could use it, if nothing on that drive is mounted. For those cases you then can download it from synaptic.

Better to use  a liveCD or the Gparted liveCD in most cases.

---

### Post by jrev on 2009-10-09
Very good answers, thank you :P

But you forgot the second part of the question :

On my Asus 701 4G I have 2.65 Gio used on a total of 3.51 Gio, that is 860 Mo available.

I bought a 8 Gio SD card to help sharing the system, but I don't know how to manage it.

Could you give me another good answer ?

I have 252 updating files to download and 195 Mo space to provide.
Shall I start the process ?

Many thanks to come :P

---

### Post by egalvan on 2009-10-09
> **oldfred said:**
> It makes sense that gparted is not normally installed as** you cannot run it from anything that is mounted.** If you have a second drive you possibly could use it, if nothing on that drive is mounted.

Better to use  a liveCD or the Gparted liveCD in most cases.

You can **RUN** gparted on ANYTHING, mounted or un-mounted.

You cannot **MAKE CHANGES** to a mounted partition.
And changes are only made after you APPLY them.

I use gparted to check disk space, as the Disk Usage Analyzer is not really useful TO ME.
gparted also shows drive definitions, file types, and mount points,
among lots of other information.

And I use PartedMagic to do any partition EDITING.
Great little distro. Always has the most up-to-date gparted.


I really miss TreeSize from the Windows world.

P.S.
There are a LOT of programs that will mess up your computer if you do not know what you are doing, gparted is just one of many. :)

---

### Post by jrev on 2009-10-09
Yes, indeed !

---

### Post by m4tic on 2009-10-09
Appplications->add/remove-> search for gparted

---

### Post by dwasifar on 2009-10-09
If the point of wanting gparted is just to see drive information, System Monitor also has an option for that.  System>Administration>System Monitor and click the File Systems tab.

Regarding your 8GB card, the system should mount it automatically at /media/disk (or something similar) when you insert it, or at boot time if it is already inserted.  You will want to use it for storage, not programs.  This means you should mainly be moving things that are stored in your home directory, like say media files, documents, or photos.  Don't try to use it for binaries or system libraries; it will make your system unacceptably slow at best, and unstable at worst.

---

### Post by jrev on 2009-10-09
> **dwasifar said:**
> If the point of wanting gparted is just to see drive information, System Monitor also has an option for that.  System>Administration>System Monitor and click the File Systems tab.

Regarding your 8GB card, the system should mount it automatically at /media/disk (or something similar) when you insert it, or at boot time if it is already inserted.  You will want to use it for storage, not programs.  This means you should mainly be moving things that are stored in your home directory, like say media files, documents, or photos.  Don't try to use it for binaries or system libraries; it will make your system unacceptably slow at best, and unstable at worst.

So there is no solution for my eeebuntu Netbook remix OS ?

The only solution beeing to find out a lighter OS ?

Something with the LXDE windows manager ?

---

