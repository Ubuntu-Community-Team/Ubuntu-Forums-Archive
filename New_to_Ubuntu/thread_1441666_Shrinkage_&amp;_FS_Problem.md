---
title: "Shrinkage &amp; FS Problem"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by gremlinkurst on 2010-03-29
Linux experience level: Newbie 2 Linux, thrilled with U-9.10
Windows/other experience level: Win 3.1-Vista (incl. server and pro editions), programming & design, application & web development, file management & graphics, & security
:popcorn:
End goal of solution to this thread: Create a Windows-recognized (File System) partition upon which I may install Windows 7, which will enable me to delete all other partitions, and then expand the single partition to reclaim all then-unallocated space (unlike previous versions of Windows, Seven cannot format partitions of an unrecognized FS (File System). Note: I'm installing Ubuntu on a machine other than this one, which [QED] is running Karmic Koala, because Linux has a lot to offer that Windows does not.

Question: I have Palimpest, GParted, and NTFS Configuration Tool but cannot figure out how to shrink this partition to make room for another, and I'm afraid to fiddle-fart with the smaller extended/swap partition, and I'm pretty sure that if I try to unmount this one and reformat it...well, the problem is obvious; it would be like intending to perform a surgical procedure on myself and administering a general anesthetic, and then being shocked I couldn't operate.  Another thing that confuses me is that I recall accessing a GUI which enabled me to shrink partitions when I first started out (a few months ago) on Linux, but can't find it (I was ignorant of how to use it, so I wisely refrained), and it's possible I'm remembering something from one of the other five Linux distros I tested (Ubuntu was the best fit for me).

What forced me to enter the Linux world is the fact that HP Recovery manager doesn't work; it kept trying to install Vista on a 32 GB partition when the HDD was 160 GB, and of course the installation [COLOR=Red]failed.  **Every time**[/COLOR].  Because of my gaming and graphics application investments, I have no choice but to build a dual-boot Windows/Linux system.  This laptop is not suitable because it's three years old and is not up to modern hardware requirements of newer applications.  The other system isn't ready yet, but eventually this laptop will be dual-boot as well...when I get another drive and battery for it.  For now, I want to test Windows Seven on this machine...but can't because the file system is unrecognized.

Moderator: If I have posted this in the incorrect forum, please move it and notify me of putative move.

Everyone: Thanks for your forthcoming and undoubtedly invaluable assistance.

---

### Post by mikeyphi on 2010-03-29
Welcome!

If I understand - you want to work on a partition but it's in use.

If that's correct, use a Live CD, or a Live USB drive, and use Gparted to resize the partition - which won't be in use since you're using a Live CD.

If I've missed the point - please say!

---

### Post by Sceiron on 2010-03-29
> **gremlinkurst said:**
> 
End goal of solution to this thread: Create a Windows-recognized (File System) partition upon which I may install Windows 7, which will enable me to delete all other partitions, and then expand the single partition to reclaim all then-unallocated space (unlike previous versions of Windows, Seven cannot format partitions of an unrecognized FS (File System). Note: I'm installing Ubuntu on a machine other than this one, which [QED] is running Karmic Koala, because Linux has a lot to offer that Windows does not.


You could boot your lap-top with win7-cd, and then DELETE all partitions within the win7 setup menu.
If you delete the partitions, it will be possible to install win7. I did this yesterday, and the HDD was ext3 all of it.

This ofcourse presuppose you must erase what's on your harddrive.
But installing win, before ubuntu is allways better in my experience. ( if one wants do dual boot)

---

### Post by shindou01 on 2010-03-29
> **Sceiron said:**
> You could boot your lap-top with win7-cd, and then DELETE all partitions within the win7 setup menu.
If you delete the partitions, it will be possible to install win7. I did this yesterday, and the HDD was ext3 all of it.

This ofcourse presuppose you must erase what's on your harddrive.
But installing win, before ubuntu is allways better in my experience. ( if one wants do dual boot)

Yep, that's what I did, and now I'm thinking of completely removing my Windows 7 Ultimate Edition.....(what a waste).....

---

