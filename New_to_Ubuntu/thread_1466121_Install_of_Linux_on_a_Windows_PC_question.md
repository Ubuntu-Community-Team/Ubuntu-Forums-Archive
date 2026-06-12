---
title: "Install of Linux on a Windows PC question"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by josephfuentes on 2010-04-30
I just got the latest copy of Ubuntu 10.04 and I was going to install it on my Windows PC. 

I have a 320GB HD which was an upgrade for me from a 160HD that I had.

My preference was to have a dual boot machine however when choosing that option during the install process *using a live CD* the installer stated it would by default in my case allocate 186GB to Windows.  For me that's sacrificing too much Windows space since getting more room was the reason to upgrade to a 320GB HD in the first place!

The other options were not viable for me since I didn't want to devote the whole disk to Ubuntu and I didn't just want to run from the CD. Choosing the advanced option I wasn't comfortable with since I'm not an advanced user. If I was I'd give Ubuntu just like 40GB HD space to play with it.

So here are my questions.

Is there a way to tell the installer only allocate X GBs of HD space to Ubuntu?

How about Wubi? I hear with Wubi you can install Ubuntu as an app under Windows just like Word or Powerpoint. And can be removed just like any other Windows app.  If this is the right app, can I use Wubi to install Ubuntu 10.04 as an app under Windows?

How does this work?

Thanks in advance !

---

### Post by madjr on 2010-04-30
there should be a slider 

to allocate X GB

just move the slider

you should also read this (the partitioning section, about halfway), pretty easy to follow

[http://www.dedoimedo.com/computers/ubuntu-install.html](http://www.dedoimedo.com/computers/ubuntu-install.html)

also grab a fresh copy of the official ubuntu manual (good beginners guide)

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by mastablasta on 2010-04-30
You can just move the slider i believe and alocate more space to Windows that way. I installed it on 60GB HDD and linux proposed to take 45 or something but i reduced it to 30 GB.
 
 
 
Wubi is not really a good idea. It's more like to try it and some things might not work well. Dual boot is a better option as you really get a working system.
 
Either way i suggest you read this free e-book and follow the easy GUI instructions:
[[COLOR=#444444]http://www.ubuntupocketguide.com/[/COLOR]]("http://www.ubuntupocketguide.com/")
 
It iwll give you all information on how to prepare the windows disk for dual boot, alocate more or less space to linux...

---

### Post by captincrash on 2010-04-30
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

A guide that I found handy when setting up my Dual-Boot system.

---

### Post by golanbatrac on 2010-04-30
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by QIII on 2010-04-30
golanbatrac posted a good link.

Included in it is this

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

Take heed.  Defrag twice and resize you Windows partitions using Windows tools in Windows.  Use the free space left after that for your Linux partitions.

If you do it any other way, you don't know what you might be destroying by being a ham-handed lummox with an ax.

---

### Post by Vined Adobo on 2010-04-30
> **josephfuentes said:**
> I just got the latest copy of Ubuntu 10.04 and I was going to install it on my Windows PC. 

I have a 320GB HD which was an upgrade for me from a 160HD that I had.

My preference was to have a dual boot machine however when choosing that option during the install process *using a live CD* the installer stated it would by default in my case allocate 186GB to Windows.  For me that's sacrificing too much Windows space since getting more room was the reason to upgrade to a 320GB HD in the first place!

The other options were not viable for me since I didn't want to devote the whole disk to Ubuntu and I didn't just want to run from the CD. Choosing the advanced option I wasn't comfortable with since I'm not an advanced user. If I was I'd give Ubuntu just like 40GB HD space to play with it.

So here are my questions.

Is there a way to tell the installer only allocate X GBs of HD space to Ubuntu?

How about Wubi? I hear with Wubi you can install Ubuntu as an app under Windows just like Word or Powerpoint. And can be removed just like any other Windows app.  If this is the right app, can I use Wubi to install Ubuntu 10.04 as an app under Windows?

How does this work?

Thanks in advance !

Windows 7 and Vista have means to shrink partitions.  To do this, you can't have any files closer to the end of the drive than the amount of space you want to use for another partition.  I have done this on 2 of my computers.  Vista let me do it from Windows.  7 had a file (which was used ONLY when the OS was running) right at the end of the hard drive and would not allow me to shrink.  For the Windows 7 netbook, I had to use gparted from the ubuntu live disk.  If you have unused space on your drive (like when Windows was installed or when you shrink a partition,) Ubuntu can handle it. If you do any of your own partitioning when you install Ubuntu, you have to do it manually--but that's somewhat advanced.  Many people find this useful so they can place the home directory in its own partition (and then not format that partition when Ubuntu is upgraded.

I haven't used WUBI and don't know how it works.  You can google for how-tos and find out all about these subjects.

Be VERY careful and backup ALL your important files before attempting anything.

Dave

---

