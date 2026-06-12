---
title: "Why Ubuntu Installation shows half hdd as one partition?"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Rushyang on 2010-10-23
Hey guys,

I have Toshiba Satellite L640 Laptop just I just bought some days before. and I have Windows 7 x64 Ultimate as current OS. 
My Problem is, I have 3 Partition in for windows 7 and I kept 30GB for ubuntu while formatting windows7. and 2 GB for unallocated space. (In Total 5: 1 for Windows 7, 2 for data, and 2 for Ubuntu Installation).

While, I was booting into ubuntu 10.10 CD for separate installation, I wasn't able to use that 2GB partition as swap space.. So I booted into Windows 7 and used and formatted that 2GB partition as NTFS disk type. At that Time, Windows 7 asked me whether I'm sure for keeping those partition as dynamic.. I just said "yes".. 
[B]
Now, beside that Windows 7 installation partition, All of my 212 GB hdd space which contains actually 4 Partitions in windows, shows as single partition in linux installation. 
[/B]

I tried EASUS Partition software into Windows 7.. but it didn't let me change anything.. 

Question: how do I get detect my 30GB partition + 2GB NTFS partition , (which are dynamic into Windows 7, ) separate into Ubuntu installation rather than single? 

Please reply fast.. Sorry for all story.. But I just wanted to be more clear so that I can get solution ASAP.

Regards,

---

### Post by plucky on 2010-10-23
You are only allowed 4 primary partitions maximum on one disk drive.So if all the partitions are primary,you will not be allowed to create another partition.

Boot the live CD and run from **System > Administration > Gparted** and post the picture that it shows of your partition scheme.

One of your partition needs to be an extended partition,in which you can create many logical partitions.

---

### Post by srs5694 on 2010-10-23
A Windows "dynamic disk" is one or more partitions that are linked together and re-allocated in other ways. This is also known as Logical Disk Management (LDM), and is very similar to the Linux Logical Volume Manager (LVM) system.

If you're using LDM/dynamic disks, the result will be that you'll probably see fewer partitions in Linux than Windows claims there are. In an extreme case, it'll look like the whole disk is one partition in Linux, but Windows could show dozens. Linux can supposedly access LDM via the same mechanism it uses for LVM -- the Windows dynamic disks will show up in /dev/mapper. Re-allocating the space in Linux will be hard, though. If you've got sufficient free space (that's not in any partitions), you'll be OK; just install Linux normally (you may need to use the manual partitioning option), and if you need to access Windows files, do it by mounting the /dev/mapper device files.

If you need to allocate space for Linux (that is, if the whole disk is tied up in the LDM), it could be trickier. I'm not sure how to shrink a Windows LDM partition, or if it's even possible. I do know that a program called [Partition Wizard](http://www.partitionwizard.com/) is supposed to enable conversion of dynamic disks to conventional partitions ("basic disks," in Microsoft parlance); however, I've never tried this myself, so I don't know how well it works.

Also, plucky is correct that you're limited to four primary partitions, so if the disk has that many primaries, you may have to do more juggling to get things to work. It's not clear to me that this is the case, though. If you've got three or fewer primary partitions, you can create an extended partition in the disk's free space and create as many logical partitions as you like within the extended partition.

If you need more advice, boot the Ubuntu installer into live CD mode, open a shell prompt (terminal), and type "sudo fdisk -lu". Post the output here, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

### Post by Rushyang on 2010-10-23
Thank you for reply guys.. I used some software in windows to convert dynamic to basic and it worked successfully.. Now I've installed ubuntu 10.10.. & both Operating Systems work just fine!

---

