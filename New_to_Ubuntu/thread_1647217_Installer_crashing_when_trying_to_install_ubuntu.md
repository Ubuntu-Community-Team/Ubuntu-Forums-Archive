---
title: "Installer crashing when trying to install ubuntu"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by QuentinK on 2010-12-17
I wish I could get a screenshot, but since it's on my LiveCD I don't think it'd work out.

But.
When I try to run my LiveCD and install Ubuntu so that it dualboots with Windows XP, the installer stops, gives me an error (Errno: 5) and then crashes back to the desktop. I've tried 3 different times to install, all with the same result.
Some more details:
I dedicated like 72gb to my Windows Partition, 6gb to my Linux (yet to be installed) partition, and like 1 or 2 gb for the swap.
I'm running off a LiveCD (flash drive)
I just recently reinstalled Windows from a previous error in which Linux took over my hard drive, so I'm skeptical about letting try and install it along side Windows again.

Any help on this is greatly appreciated!

~Quentin

---

### Post by Dutch70 on 2010-12-17
Did you burn the disc slow and check it?

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by candtalan on 2010-12-17
> **QuentinK said:**
> When I try to run my LiveCD and install Ubuntu so that it dualboots with Windows XP, the installer stops, gives me an error (Errno: 5) and then crashes back to the desktop. I've tried 3 different times to install, all with the same result.

a report here found that some download sources (mirrors) are bad. Be sure to check MD% and or try other mirrors?
[http://ubuntuforums.org/showthread.php?t=1313742](http://ubuntuforums.org/showthread.php?t=1313742)

> 
Some more details:
I dedicated like 72gb to my Windows Partition, 6gb to my Linux (yet to be installed) partition, and like 1 or 2 gb for the swap.
I'm running off a LiveCD (flash drive)
I just recently reinstalled Windows from a previous error in which Linux took over my hard drive, so I'm skeptical about letting try and install it along side Windows again.

Same thing happened to me unfortunately. For me it was this bug, one particular installer choice will zap you.
Maverick installer lost Windows partitions
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/659106](https://bugs.launchpad.net/ubuntu-release-notes/+bug/659106)

If you have already created empty partitions, then the Maverick installer will not use them in 'side by side', it will itself make a choice of one existing partition and offer to resize. The resize works ok and is safe, But the button to choose the whole partition has the disastrous bug. 

Once you have a checked 'good' live media, then the installer choice for you will be the 'advanced' choice. It is  not as difficult as you might think. Take your time. Just identify first your Windows partition and any partition you want to preserve. Windows might be device sda1 72GB,  /dev/sda1 that is: on drive 'a', on the first partition.

If you have created say partitions /dev/sda2 (6GB) and /dev/sda3 (1GB) then in the advanced installer, change 
/dev/sda2 to be formatted during install and mount point as  /

And change /dev/sda3 to be mounted as swap.

Finally check again that you changed the partitions you needed to and not Windows, then proceed.

---

### Post by QuentinK on 2010-12-17
I did the MD5sum check and it came out with the hashes are the same so I'm assuming that's good.
And last night when I was trying to install it, I made sure to format the partition, select "/" as the mount point, and it still didn't work.
I'm gonna try to format the flash drive I used as the LiveCD and install it onto it again, to see if that works.

---

### Post by candtalan on 2010-12-17
> **QuentinK said:**
> I did the MD5sum check and it came out with the hashes are the same so I'm assuming that's good.
And last night when I was trying to install it, I made sure to format the partition, select "/" as the mount point, and it still didn't work.
I'm gonna try to format the flash drive I used as the LiveCD and install it onto it again, to see if that works.
Was the md5sum the same as here
a8d8e24bf8b82b4302d074fcac380d65 *ubuntu-10.10-alternate-amd64.iso
419ad8ee1bb76a49490f4a08b5be43f0 *ubuntu-10.10-alternate-i386.iso
1b9df87e588451d2ca4643a036020410 *ubuntu-10.10-desktop-amd64.iso
59d15a16ce90c8ee97fa7c211b7673a8 *ubuntu-10.10-desktop-i386.iso
6877bf8d673b87ba9500b0ff879091d0 *ubuntu-10.10-netbook-i386.iso
ab66a1d59a8d78e9ea8ef9b021d6574a *ubuntu-10.10-server-amd64.iso
ce1cee108de737d7492e37069eed538e *ubuntu-10.10-server-i386.iso
d1db1f93bb7486593b7d1ea023c0e3f8 *wubi.exe

Recall an earlier comment from a link where it was reported that some mirrors were found to have bad images? So checking a CD against its burn file will  not prove you have a 'good' image.
hth

---

### Post by wilee-nilee on 2010-12-17
Before you try installing again, do you know the number of primary partitions on the HD now. Your only allowed 4 on one HD. from the live Ubuntu cd post the output of
```
sudo fdisk -lu
```

Even better run the bootscript from the link in my signature and post all the text from the generated file in code tags as described in the sig as well.

---

### Post by QuentinK on 2010-12-18
> Was the md5sum the same as here
a8d8e24bf8b82b4302d074fcac380d65 *ubuntu-10.10-alternate-amd64.iso
419ad8ee1bb76a49490f4a08b5be43f0 *ubuntu-10.10-alternate-i386.iso
1b9df87e588451d2ca4643a036020410 *ubuntu-10.10-desktop-amd64.iso
59d15a16ce90c8ee97fa7c211b7673a8 *ubuntu-10.10-desktop-i386.iso
6877bf8d673b87ba9500b0ff879091d0 *ubuntu-10.10-netbook-i386.iso
ab66a1d59a8d78e9ea8ef9b021d6574a *ubuntu-10.10-server-amd64.iso
ce1cee108de737d7492e37069eed538e *ubuntu-10.10-server-i386.iso
d1db1f93bb7486593b7d1ea023c0e3f8 *wubi.exe

Recall an earlier comment from a link where it was reported that some mirrors were found to have bad images? So checking a CD against its burn file will not prove you have a 'good' image. Yup, checked it against the 4th one down and it was all clear.

> Before you try installing again, do you know the number of primary partitions on the HD now. Your only allowed 4 on one HD.  I only have one primary on my HDDm and that's my windows partition. Also considering I only have 3 partitions in total, I don't think that would be a problem.

I downloaded the LiveCD .iso file from [[COLOR="Navy"]ubuntu.com[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download"), so I sure hope their download link is reliable.

I'll try to download and mount it onto my flash drive again to see if it works.

---

### Post by candtalan on 2010-12-19
Sorry to hear you are still having problems. Very good that you have been able to confirm the md5sum. 
Which machine did you use to check the md5sum?
This thread subject is misleading because as I see it, you are unable even to RUN the live CD at all, which is a precursor to the intended Install. Not being able to run a Live CD is different from not being able to 'install'. For example, running a live CD does not have any partitions problems, yet people are responding about them here.
I cannot see that you can get far unless you check  your basics like the CD drive itself (in another machine), look at function of bios edit (working motherboard?). Remove all HD connections, use a different CD drive and then try the CD as a live session with no HD connected at all, etc etc.

You are sure that the CD is burned correctly (MD5), so start from there. Get confidence by using it in other machines. At this stage it seems as if something is basically wrong with the hardware or whatever, with the CD drive looking like the first possibility. Blue sky thought: When the CD runs, the power supply voltage dips, so it cuts power, so it does a restart???.... etc etc. Need some careful experiments here.. HTH

---

### Post by amjjawad on 2010-12-19
> **candtalan said:**
> Sorry to hear you are still having problems. Very good that you have been able to confirm the md5sum. 
Which machine did you use to check the md5sum?
This thread subject is misleading because as I see it, you are unable even to RUN the live CD at all, which is a precursor to the intended Install. Not being able to run a Live CD is different from not being able to 'install'. For example, running a live CD does not have any partitions problems, yet people are responding about them here.
I cannot see that you can get far unless you check  your basics like the CD drive itself (in another machine), look at function of bios edit (working motherboard?). Remove all HD connections, use a different CD drive and then try the CD as a live session with no HD connected at all, etc etc.

You are sure that the CD is burned correctly (MD5), so start from there. Get confidence by using it in other machines. At this stage it seems as if something is basically wrong with the hardware or whatever, with the CD drive looking like the first possibility. Blue sky thought: When the CD runs, the power supply voltage dips, so it cuts power, so it does a restart???.... etc etc. Need some careful experiments here.. HTH

As per the OP's posts, he's using USB Drive to Install but he's calling it LiveCD instead of LiveUSB.

---

### Post by amjjawad on 2010-12-19
> **QuentinK said:**
> I wish I could get a screenshot, but since it's on my LiveCD I don't think it'd work out.

But.
When I try to run my LiveCD and install Ubuntu so that it dualboots with Windows XP, the installer stops, gives me an error (Errno: 5) and then crashes back to the desktop. I've tried 3 different times to install, all with the same result.
Some more details:
I dedicated like 72gb to my Windows Partition, 6gb to my Linux (yet to be installed) partition, and like 1 or 2 gb for the swap.
I'm running off a LiveCD (flash drive)
I just recently reinstalled Windows from a previous error in which Linux took over my hard drive, so I'm skeptical about letting try and install it along side Windows again.

Any help on this is greatly appreciated!

~Quentin

Ok, first thing first, what's the capacity of your RAM? you just mentioned some info about your HDD but you didn't mention the other hardware like CPU, RAM and Graphics Card.

Second of all, how exactly did you create the LiveUSB (NOT LiveCD)? 
I assume you followed the instructions given here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
You can find all the needed instructions to create either LiveCD/LiveUSB.

You're confirming that MD5SUM is correct  so that's fine.

I prefer to post the result of the command that Wilee suggested, just to make sure your partitions are ready OR you could take a screen shot to your partitions while you're on GParted (System > Administration > GParted). It would be helpful for us to understand even better.

By the way, while you're on the Live Session, you're very much able to take a screenshot. I do that all the times.

Edit: I once created LiveUSB for Ubuntu 10.10 as per the instructions given in Ubuntu's website but it didn't work and crashed as well. I then created the LiveUSB using [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and it worked. You may want to try that as an alternative.

---

### Post by candtalan on 2010-12-19
Whoops. Thanks for pointing it out.

---

