---
title: "Ive looked everywhere for the answer and cant find it, please help."
date: 2009-11-22
forum: New to Ubuntu
---

### Post by vault55 on 2009-11-22
Just had a all options Thinkpad T400 built and I would like to split the 500gb hard drive in two. Half win7 and other 9.10 Ubuntu (dual booting), my question is if I partician it into two parts and it turns out something gets messed up, will I be able to use my Lenovo Rescue & Recovery tool to recover both partitions and restore this laptop back to its original state?
 
Ive read many posts that say that the rescue and recovery portion could get messed up due to the GRUB writting to the MBR or something like that (not to familiar with all of the terminoligy or this process). Any assistance you can provide would be appreciated. Ive searched these forums and google and now I just have to ask and hope. Thanks:KS

---

### Post by sandyd on 2009-11-22
if your installing karmic (ubuntu 9.10)
this should not be a problem for you
this is because the new Grub Loader (grub2) detects and automatically adds recovery partitions (in fact, any partition that is bootable, including my hidden dell recovery partition that was not avalable from the windows bootloader)

---

### Post by skatinjj on 2009-11-22
I would first make system discs before you do anything just in case the recovery partition does get messed up somehow.

---

### Post by Scott753 on 2009-11-22
Installing Ubuntu when you already have Windows installed is usually less problematic than vice versa. The Ubuntu installation CD will partition your hd for you, and as for whether the Lenovo Recovery tool will work properly, well, you should have no problem getting it to open, since your computer will boot to CD as first priority, but I don't really know how well it will work.

If worst comes to worst, at the very least you will be able to recover your data from both partitions, and do a complete reinstall of both OS's. But that's an extreme last resort. Many people run dual boots with no problems.

---

### Post by vault55 on 2009-11-22
Thanks Carlee, I had no idea that the problem was addressed with GRUB2 but I want to make sure were on the same page here. If one day I want to take my laptop back to out of the box settings would I do this as I have always done by using the Rescue and Recovery partition in my Think pad? Whay would GRUB2 add another recovery partition as you mentioned?
 
Skatinj-I'm making the backup disk as we speak and they gave me a downgrade for XP (but I actually love Win7)
 
Scott753-the Recovery is built into the computers HDD, many people run dual boots will no problems but when they do have problems they often find they cant use the "well, I'll just simply wipe and reinstall" that ease may not work if 1. it becomes corrupt by Ubuntu MBP or 2. doesn't wipe and reformat the partition that Ubuntu is on
 
I just want to male sure before I commit to doing this on this machine any MANY others like it, that its possible using the Rescue and Recovery partition to resore this computer back to factory out of the box state. thanks again

---

### Post by sandyd on 2009-11-22
> **vault55 said:**
> Thanks Carlee, I had no idea that the problem was addressed with GRUB2 but I want to make sure were on the same page here. If one day I want to take my laptop back to out of the box settings would I do this as I have always done by using the Rescue and Recovery partition in my Think pad? Whay would GRUB2 add another recovery partition as you mentioned?
 
Skatinj-I'm making the backup disk as we speak and they gave me a downgrade for XP (but I actually love Win7)
 
Scott753-the Recovery is built into the computers HDD, many people run dual boots will no problems but when they do have problems they often find they cant use the "well, I'll just simply wipe and reinstall" that ease may not work if 1. it becomes corrupt by Ubuntu MBP or 2. doesn't wipe and reformat the partition that Ubuntu is on
 
I just want to male sure before I commit to doing this on this machine any MANY others like it, that its possible using the Rescue and Recovery partition to resore this computer back to factory out of the box state. thanks again
it will add  a menu item in the bootloader (actually be careful, i accidentally hit enter on the recovery partition entry when i was sick and just stopped it in time...) that will allow you to boot to the partition.

however, although im 80% shure, you should wait and see if other people have tried this. (with karmic)

and yes, i tried recovering from the menu. only once though. and it was successful. 

P.S.: Important Hint: resize the windows partition with the partition editor/manager that windows provides (assuming this is >=Vista) because windows can be quite picky and give an error just because you were mucking around with its partitions. Just resize it and leave unformated, unpartitioned free space for ubuntu. Then when installing ubuntu, choose the option "use largest contineous block of free space) (or something close to that, i havent used that thing for a while now)

---

### Post by vault55 on 2009-11-23
Thanks, if I ever attemp to do a complete reinstall using Rescue and Recovery, will it erase my Ubuntu partitian and make my computer all Windows 7 again? This is what i need to know for sure before I install.  I really appriciate you taking the time to answer my questions.

---

### Post by sandyd on 2009-11-23
> **vault55 said:**
> Thanks, if I ever attemp to do a complete reinstall using Rescue and Recovery, will it erase my Ubuntu partitian and make my computer all Windows 7 again? This is what i need to know for sure before I install.  I really appriciate you taking the time to answer my questions.
no. it will not delete the ubuntu partition.
you will need to manually delete the windows AND the ubuntu partition using gparted (from livecd)

---

### Post by Mark Phelps on 2009-11-24
> **vault55 said:**
> Just had a all options Thinkpad T400 built and I would like to split the 500gb hard drive in two. Half win7 and other 9.10 Ubuntu (dual booting), my question is if I partician it into two parts and it turns out something gets messed up, will I be able to use my Lenovo Rescue & Recovery tool to recover both partitions and restore this laptop back to its original state?
Basically -- yes and no.  The R&R tool will restore your Win7 installation, most probably wiping the drive and repartitioning it in the process.  But no, it will not restore the Ubuntu installation.  It will most likely erase it.
 
> Ive read many posts that say that the rescue and recovery portion could get messed up due to the GRUB writting to the MBR or something like that (not to familiar with all of the terminoligy or this process).

Unless you go out of your way to install GRUB to the Ubuntu partition, it will overwrite the MBR that Win7 has there at present.  That will not damage your R&R ability, but if you have to repair Win7 in the future, doing that will replace the MBR and wipe out the GRUB info in the process.

Before you do ANYTHING to Win7, you would do best to see if you can back off an image to an external drive using the builtin Backup capability.  That way, if the whole thing goes south, you will be able to restore your current setup without losing anything.

Use the Win7 builtin function to create and burn a Recovery CD.  That will allow you to repair the boot loader without wiping out your installation.

Also, do NOT use the Ubuntu installer to shrink the Win7 partition.  Doing so risks corrupting the Win7 partition and rendering it unbootable.

---

### Post by oingk on 2009-12-30
> **vault55 said:**
> Thanks, if I ever attemp to do a complete reinstall using Rescue and Recovery, will it erase my Ubuntu partitian and make my computer all Windows 7 again? This is what i need to know for sure before I install.  I really appriciate you taking the time to answer my questions.


I have Thinkpad SL500 preinstalled with Windows XP Pro, I also installed Ubuntu 9.10 (dual boot created with the help of the installation CD, GRUB2 taking over MBR):

-When I switch on my computer it gets to GRUB2's menu, I can chose either Windows XP, Ubuntu, Ubuntu Recovery, and the Rescue and Recovery partition (and two other partitions that seem to be different versions of Ubuntu but I can't log into them and two partitions called "memory test", I don't know what all these are and why they are there). I can get into XP, Ubuntu or RnR.

-The Rescue and Recovery utility is still there but doesn't function. I tried using it and it *doesn't *restore everything to what it was. It doesn't affect Ubuntu at all. Only thing it does is restore the Windows XP partition to what it was. In addition, I can not use the Backup finctionality of RnR. If I try to the program crashes.

Maybe this info helps you. Personally I am still trying to figure out if there is a way to do this dual boot while having the ability to backup everything inlcuding Ubuntu all using R&R.

From info I could find however, the R&R only works for Windows. I'm still researching the subject though.

---

### Post by vault55 on 2009-12-30
> **oingk said:**
> I have Thinkpad SL500 preinstalled with Windows XP Pro, I also installed Ubuntu 9.10 (dual boot created with the help of the installation CD, GRUB2 taking over MBR):

-When I switch on my computer it gets to GRUB2's menu, I can chose either Windows XP, Ubuntu, Ubuntu Recovery, and the Rescue and Recovery partition (and two other partitions that seem to be different versions of Ubuntu, I don't know why they are there). I can access any of these partitions.

-The Rescue and Recovery utility is still there but doesn't function. I tried using it and it *doesn't *restore everything to what it was. It doesn't affect Ubuntu at all. Only thing it does is restore the Windows XP partition to what it was. In addition, I can not use the Backup finctionality of RnR. If I try to the program crashes.

Maybe this info helps you. Personally I am still trying to figure out if there is a way to do this dual boot while having the ability to backup everything inlcuding Ubuntu all using R&R.

From info I could find however, the R&R only works for Windows. I'm still researching the subject though.


As far as I know thats correct, the RR only works for Win and you wouldnt want to mix the two anyway.  I have read about all of this until its put me to sleep many nights over again.  The conclusion that Ive come to is back up Linux stuff that you want to save on an external or large USB because your going to want to do a "fresh" install when they do the next release (which occurs every six months).

  If anyone is smarter on this subject, feel free to educate us. thanks

---

### Post by oingk on 2010-01-04
hi just wanted to say that maybe this thread interests you:
[http://ubuntuforums.org/showthread.php?t=1371421](http://ubuntuforums.org/showthread.php?t=1371421)

---

### Post by Methuselah on 2010-01-04
If you have any data you cannot afford to lose please back up to secondary storage device before interfering with hard drive partitions.
In fact, taking an image of the whole disk would be the best option.
It'll give you useful insurance against a mistake in a moment of absentmindedness.

---

### Post by buntutu on 2010-01-04
I've come across something called clonezilla which is a backup/recovery tool.  It will back up your Windows and Ubuntu.  I've not used it yet though I intend to, so I can't advise you on it other than to give you a link:  [http://clonezilla.org/](http://clonezilla.org/)

---

