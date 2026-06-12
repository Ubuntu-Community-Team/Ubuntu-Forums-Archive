---
title: "Ubuntu10.10 Grub issue - (Was working fine until it updated moments ago some files )"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by tazmenia on 2010-11-07
Hello,
I have a laptop containing 1 partition C: with windows 7 on it.
A week ago I downloaded Ubuntu10.10 iso image mounted and installed it via windows7 using wubi and chose the option ( install inside windows ).
It worked great over the week I get the choice prompt between windows 7 or Ubuntu at startup I installed softwares on ubuntu it was running smooth no problems.
Until moments ago some updates recommendations of 122mb downloaded and installed, It required restart , so i reboot and pick Ubuntu then I find myself stuck on the Grub> command , I looked up this issue and tried some suggested solutions, none worked.
I tried the grub> linux /boot/vmlinuz-(kernel version ) I couldnt figure out my kernel version they told me toclick tab and it will auto complete , that didnt work as it couldnt even see /boot/ , so I tried the other solution replacing the wubildr file by another recommended that once replaced inside C:\ and rebooted that I can pick Ubuntu and it will boot just fine , that solution didnt work either the only change was that I got a different version of grub and when I tabbed I could see the folders of c:.
I need Urgent help with this matter please.

---

### Post by tazmenia on 2010-11-07
I am in a desperate need regarding this matter , please. I got my Postfix mail server project to return tomorrow.

---

### Post by bcbc on 2010-11-07
If you get stuck at a grub prompt you can boot the wubi install manually.

ls (small LS) lists the partitions.

One of these is the windows host partition and contains the root.disk (virtual disk for wubi).
Try each one until you find it e.g.
```
ls (hd0,1)/ubuntu/disks/root.disk
```

Once you have it, remember the drive/partition e.g. (hd0,2) and map this as follows:
(hd0,1) = /dev/sda1
(hd0,2) = /dev/sda2
(hd1,1) = /dev/sdb1

Ok now boot manually using e.g. (hd0,2) and /dev/sda2:
```
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

If you just need to get data off the root.disk, use a program called ext2read - it can view the root.disk's contents in readonly mode (just point it at c:\ubuntu\disks\root.disk)

---

### Post by tazmenia on 2010-11-08
I followed your instructions 
I found out by using the <tab> that /ubuntu/ is found on (hd0,3)
but once I run the code it says:
 
error: fixup signature not match
 
could it be because I replaced the wubildr file with another in C:\ ?
 
if so how can I restore the original wubildr file ( can system restore on Win7 work? )
 
I have also tried the set root but on loopback I get the same error 
fixup signature not match
I tried 
configfile (hd0,3)/ubuntu/winboot/wubildr.cfg
it tells me it cannot boot from the image to run windows and chkdsk /r
 
or if its not because of the new wubildr file what's the solution?

---

### Post by tazmenia on 2010-11-08
I could really use some help with this, now Im even interested to understand the problem.

---

### Post by bcbc on 2010-11-08
I would first try the following:

1. boot windows, select the drive that ubuntu is on, normally c: but it sounds like it could be d: and run chkdsk as follows:
open My Computer, rightclick on the drive, Properties, Tools, Check disk for errors, Fix automatically. 
If it's the main windows drive it will force you to reboot. 

2. If that still fails to solve it, you can try fsck'ing the root.disk. For that you'll need an ubuntu CD that you can boot in 'live CD' mode i.e. boot from it and select 'Try without installing'. Then when you get a desktop enter:
CTRL-ALT-t to get a terminal prompt
sudo mkdir /media/win 
sudo mount /dev/sda3 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk

Did something happen while you were running updates, e.g. you had to force a shutdown of the computer? 

PS I found a thread with the same error message that was solved:
[http://ubuntuforums.org/showthread.php?t=1571142](http://ubuntuforums.org/showthread.php?t=1571142)

I think I would still try my first two solutions - they won't hurt. And copying root.disk's around maybe won't be ideal either e.g. if you file system is fragmented. But if my things don't work, try what the person in the thread did and see if that works.

Good luck

---

### Post by tazmenia on 2010-11-08
Nothing happened during the update it just downloaded and installed then requested a restart so that the updates take place. I rebooted and picked Ubuntu then ended up in the grub> command prompt.
 
Regarding the Live CD , I'm afraid my Ubuntu installation was from the iso download file from Ubuntu.com the 10.10 arround 700mb and I mounted the image and ran the exec wubi file then picked the install inside windows option.
 
still running chkdsk on laptop.
However does me replacing the wubildr could have an effect on the error msg 
fixup signature not match ?

---

### Post by bcbc on 2010-11-08
> **tazmenia said:**
> Nothing happened during the update it just downloaded and installed then requested a restart so that the updates take place. I rebooted and picked Ubuntu then ended up in the grub> command prompt.
 
Regarding the Live CD , I'm afraid my Ubuntu installation was from the iso download file from Ubuntu.com the 10.10 arround 700mb and I mounted the image and ran the exec wubi file then picked the install inside windows option.
 
still running chkdsk on laptop.
However does me replacing the wubildr could have an effect on the error msg 
fixup signature not match ?
I don't think it's from copying the wubildr. The wubildr in the winboot directory is the same as the original wubildr. 
The wubildr issue is caused by the upgrade from 10.04 to 10.10 where it updates the wubildr, but the new version is corrupted.

I don't think a new 10.10 install corrupts its wubildr. I haven't seen this.

PS if you have installed your wubi to a partition other than windows e.g. so you have c:\wubildr and d:\ubuntu\winboot\wubildr then there is a bug in lupin-support that prevents the update of c:\wubildr anyway. So it's unlikely that the wubildr was updated at all.

---

### Post by KekeJr on 2011-03-22
Hello,

Despite that i am an n00b user in linux i acctualy think i can help you :D

After getting the same errors as you an trying for about 2 hour without success to restore my ubuntu install, right at the point where i restarted my PC and was about to delete my ununtu installation i did somenthing that amazed me...


```
Copy wubildr.mbr and wubildr from c:\ubuntu\winboot in c:\
From the installation disk \boot\grub copy the loopback.cfg in c:\ubuntu\boot\grub
```

If ubuntu is not installed in you're C:\ drive then replace with the correct drive
For me this worked and i hope it will work for you

---

### Post by bcbc on 2011-03-22
> **KekeJr said:**
> Hello,

Despite that i am an n00b user in linux i acctualy think i can help you :D

After getting the same errors as you an trying for about 2 hour without success to restore my ubuntu install, right at the point where i restarted my PC and was about to delete my ununtu installation i did somenthing that amazed me...


```
Copy wubildr.mbr and wubildr from c:\ubuntu\winboot in c:\
From the installation disk \boot\grub copy the loopback.cfg in c:\ubuntu\boot\grub
```

If ubuntu is not installed in you're C:\ drive then replace with the correct drive
For me this worked and i hope it will work for you
Based on the latest info, this fix works temporarily but you need to also run the Permanent Fix from here: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

