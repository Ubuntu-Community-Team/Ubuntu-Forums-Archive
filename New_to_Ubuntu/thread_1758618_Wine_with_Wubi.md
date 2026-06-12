---
title: "Wine with Wubi"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by JerryC on 2011-05-14
I have v10.10 installed by wubi in Windows 7.  I installed wine in Ubuntu and then, using wine, I installed Quicken.  My question is, is this a safe installation of Ubuntu to use for a working system or should I break down and partition the drive and do a regular install?  And why?

JC

---

### Post by Frogs Hair on 2011-05-14
I don't think this will cause a problem , The only reason I could see to use Wine on a on dual boot is if you had a really old Windows program that just won't run on Win 7 . I dual boot so I don't have to use Wine and I need Windows for other reasons. A traditional dual boot will preform better and the file system is much more stable.

---

### Post by fabricator4 on 2011-05-14
> **JerryC said:**
> I have v10.10 installed by wubi in Windows 7.  I installed wine in Ubuntu and then, using wine, I installed Quicken.  My question is, is this a safe installation of Ubuntu to use for a working system or should I break down and partition the drive and do a regular install?  And why?

JC

Additional points to those that Frogs Hair made:

At the moment your Ubuntu disk a virtual disk file that runs under Windows.  Any error with that one file and you could lose everything on your Ubuntu installation, including data.

A separate partition for Ubuntu formatted as ext4 is much more robust.  Because it's a journaling file system it's able to recover from errors better, such as those caused by a power outage.

Wubi is a great way to try Ubuntu and see if it will run on your hardware, but it's not really meant to be used as a production environment.  (It is very good though)

The time to change is when you are comfortable working in Ubuntu and want a serious installation.

You can go a step further an make a separate partition for /home as well.  This further protects you from problems and lets you install or re-install or upgrade as you wish without worrying about your data so much.

That said, you should _always_ back up all your data before changing partitions, installing, upgrading, or otherwise making large changes to the operating system.  IOW you should back up your system now before changing your hard drive to put Ubuntu in its own partition.

Chris

---

