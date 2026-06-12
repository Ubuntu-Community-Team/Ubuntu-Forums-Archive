---
title: "Hi there!! New Here"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by gaspernoe on 2011-03-27
Hi there,

Just plunged into the Ubuntu world and man has it impressed!!! Ive got a 2x Intel(R) Pentium(R) 4 CPU 2.80GHz HP Pavillion desktop with 2GB RAM.This was a old system so i decided to move on from XP to another operating system which would enhance performance.Been hearing a lot about Ubuntu, so I decided to try it out.It seems much lighter,loads waaaaaaaay faster, and doesn't feel a lot different from Windows.I basically used this desktop to browse the internet and listen to music and 

I have a few questions though and I apologise if they sound really basic.

1) **WUBI  Vs  Completely moving XP from my system and replacing with Ubuntu (Full Installation)**
 
I installed the through WUBI.
-Does this effect performance of the system(speed,graphics etc) ? If so is it very significant?

-Should I shift to the complete installation for my system(its an old desktop.)?Is this process a tedious one(I am an absolute beginner and no nothing about partitioning)?

- I hadn't de-fragmented my disk before installation(a guide advised doing so)?Is it necessary(My system though old had a lot of utilities which made sure it ran fast)?

Thanks 

G
-









A summary of my specs :

---

### Post by Lateralis on 2011-03-27
Hi there!  Welcome to Ubuntu and the Ubuntu Forums!  

Wubi is really only designed to act as a trial for Ubuntu.  Wubi installs completely within Windows but that really isn't such a great idea if you wish to use Ubuntu forever more.  The performance will be lower with a Wubi install than a fresh/clean install.  

This doesn't mean you have to ditch XP though.  You can dual boot with XP and Ubuntu side by side.  All you need to do is resize your current hard drive, keeping Windows XP in one partition and having at least two partitions for Ubuntu: one is the main system partition and the other is a "swap" partition.  There are more advance partitioning schemes but this is the most basic one.  Personally, I would advise having four partitions: Windows XP, Ubuntu, Swap and a data partition which is shared between XP and Ubuntu. 

Is partitioning and installing tedious?  Not really.  Ubuntu comes with partitioning tools so you can partition your hard drive using those.  This isn't a particularly good idea though - it is much better to use Windows' tools where possible to resize Windows partitions.  It's been a while since I used XP, but I think XP has inbuilt tools to shrink a partition.  Either way, before you do any partition, *backup all of your important data* just on the off chance something does go wrong.

---

### Post by sanderd17 on 2011-03-27
The difference between WUBI and a normal installation is mainly the boot time. Once Ubuntu is running, it's about the same.

Wubi does have one other problem though. A little problem with your windows installation can break your ubuntu installation.

I've read more than one post about people not being able to boot there ubuntu (wubi installation) and asking how they can get some important files or settings from it. 

SO in short: wubi is good for testing, but don't use it too long.

I would suggest: use wubi for now to try and learn, and in June (when most bugs of the new 11.04 will be erased), do a normal install of 11.04.

---

### Post by gaspernoe on 2011-03-27
Thanks for the swift replies :).Will partition I think. :)

---

### Post by Frogs Hair on 2011-03-27
These links may help .
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

