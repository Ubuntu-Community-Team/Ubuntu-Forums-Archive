---
title: "Uninstall Ubuntu 11.04"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by rs321 on 2011-06-22
Folks,


How do I entirely get rid of Ubuntu 11.04 until I've calmed down enough to try it again?


-Randy

---

### Post by garvinrick4 on 2011-06-23
#Use any partition management software and delete or format the partition.
Windows has one installed and linux has a few ubuntu uses "gparted'
#Have your windows recovery cd handy so you can put windows boot manager back in
place.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by rs321 on 2011-06-23
garvinrick4,

Thanks, but I don't have any partition management of which I am aware and I don't have a windows recovery disk, just the installation disk.  Nor has it ever been explained to me where I could enter lines of code, if that where to prove necessary.  I'm lost with Ubuntu but I've never studied software development, either, so I'm at a bit of a disadvantage.

I think for now I'll delete anything I can get my hands on and say screw Ubuntu until I calm down because none of the six installations I've tried so far has been worth a damn.

-Randy

---

### Post by mikenev on 2011-06-23
If you only have ubuntu on the machine right now, then you can put the windows install disk in and repartition the drive when you put windows back on.

If you dual booted windows and ubuntu, then use the windows install disk and choose the 'repair' option. There is an option to restore the boot record from there. You can delete the linux partitions when you're back inside windows. See [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

### Post by garvinrick4 on 2011-06-23
> **rs321 said:**
> garvinrick4,

Thanks, but I don't have any partition management of which I am aware and I don't have a windows recovery disk, just the installation disk.  Nor has it ever been explained to me where I could enter lines of code, if that where to prove necessary.  I'm lost with Ubuntu but I've never studied software development, either, so I'm at a bit of a disadvantage.

I think for now I'll delete anything I can get my hands on and say screw Ubuntu until I calm down because none of the six installations I've tried so far has been worth a damn.

-Randy
#I understand Randy you are on a bit of a rant because you have had trouble with installing Ubuntu. Some users install so easy and others have trouble because of driver issues. I am sorry it did not go smoothly for you and wish you the best. 
#In my signature is a pocket guide on Ubuntu in .pdf format you can read at your own time.
Also in my signature is a post install guide for all versions of Ubuntu.

---

### Post by Wim Sturkenboom on 2011-06-23
As somebody said, use the windows repair option to fix the MBR; that is the important part. If you only remove the Ubuntu partitions, Grub will complain and you can't use your system at all till you've fixed it.

Once your system boots into windows that way, use windows disk management to delete the Ubuntu partitions and use them as you like.

Note: make backups of your important data in case something goes wrong !

---

### Post by rs321 on 2011-06-26
Folks,

I fixed the problem.  My mother board and processor are both rated at 128 bit so I figured there'd be no sweat driving the 64 bit version.  What I didn't consider was perhaps a few other innards sunk deep in the bowels of the machine weren't 64 bit and thence big problems.  I downloaded the 32 bit version and it installed beautifully after just one "Repair" cycle.  It was almost PnP and I have it configured almost to my liking.  As soon as I gain a lot more knowledge I expect to have it just tickety-poo.

Thanks again for your help because I did learn enough from you that this last install looks permanent.  I'll be back, but I expect for just a few random questions.

-Randy

---

