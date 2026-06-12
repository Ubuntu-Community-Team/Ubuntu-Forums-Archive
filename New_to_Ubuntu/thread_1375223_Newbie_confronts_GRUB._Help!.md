---
title: "Newbie confronts GRUB. Help!"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Kdeeze on 2010-01-07
Hi guys, yesterday i made my first venture into Linux with Ubuntu and the help of a very informative book i picked up at Barnes and Noble. I installed version 9.04 x86-32 bit on my second SATA hard drive (the first HD having windows 7 x86 - 64 bit and third HD having media). Everything worked beautifully, GRUB allowed me to select between operating systems.

I decided i wanted to switch Ubuntu to the current version in 64 bit. Heres where i make my mistake. I deleted the entire partition that had ubuntu installed on it, thinking it would just go away and i could reformat it with the 64 bit version.

Rebooting caused GRUB with error 22 right after my BIOS starts up. My natural instinct was to get Ubuntu back on my second hard drive, i now reside with error 17 after the BIOS.

I have three sata hard drives. sda - windows 7, sdb - currently ubuntu 9.04 32 bit, and sdc - media. None are in any kind of RAID setting.

Anyone have any idea how to get good ol' GRUB back and working right? I can't even boot windows! :(

edit: my goal would be to get GRUB back up and working with a 64 bit version of 9.10 ubuntu so i can continue on my linux exploration.

---

### Post by Buuntu on 2010-01-07
When you reinstalled, did you install Ubuntu 9.04 or Ubuntu 9.10?  This is important because each of them uses a very different grub version (grub 0.97 vs grub 2 (1.97) respectively).

** I know this isn't what you asked, but just to ease your pain meanwhile, if you change the BIOS to boot off the windows HDD you should be fine and not have to deal with grub for the moment.  (I need to know what version of grub you are using before I attempt to help you).

---

### Post by khamil8686 on 2010-01-07
welcome to linux :) ive been using it for almost a year and am loving it! i use 64 bit linux and never have any problems, it will run 64 bit programs and 32 bit programs, installing the IA-32 package will save many headaches for 64 bit :) 32 bit programs require it to work right. it would have saved me a lot of headaches lol. when i reinstall ubuntu i just let the graphical installer detect the drives and partitions and then i create a partition table manually and select which partition i want to install to there, it will require a format before it installs but it will format it, you dont need to use any other tools to format, my guess is you used a different program to format the drive and it got rid of the MBR during that format (first part thats read of a hard drive) anyways to fix the grub error you will need to boot from your live cd and reinstall grub, check out this link, ive used it before :)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

if you have any questions just post back on this thread :)

-----
update
-----
the above will reinstall grub 1, not grub 2
just reread and it said you want 9.10 now, its a great release, everything worked outof the box for me :) well cept installing graphics driver but that was straight-forward.
just boot from your 9.10 boot cd, instead of doing automatic install choose to specify your partition table manually when it gives you the radio button to choose from when installing, choose the ubuntu partition (it should auto detect windows partition and your ubuntu partition) and install there! the manual partition option sounds ominous to first time users but ubuntu makes it simple to understand :)
welcome to ubuntu!

-kyle

---

### Post by Kdeeze on 2010-01-07
Thanks for the tips khamil8686, i am definatly going to stick to 64 bit once i get it working!



> **Buuntu said:**
> When you reinstalled, did you install Ubuntu 9.04 or Ubuntu 9.10? This is important because each of them uses a very different grub version (grub 0.97 vs grub 2 (1.97) respectively).

** I know this isn't what you asked, but just to ease your pain meanwhile, if you change the BIOS to boot off the windows HDD you should be fine and not have to deal with grub for the moment. (I need to know what version of grub you are using before I attempt to help you).


Currently i have 9.04 installed, but i am sitting at work right now contemplating what to do when i get back to my PC. I have the install cd for ubuntu 9.10 so i am going to install that on my Ubuntu HD and get rid of 9.04. Do you think this could solve my GRUB error? I have read that the new version of GRUB overlooks many things like what i am going through. But, i don't understand why i would still be recieving this error because i am technically back to my settings i had when GRUB was working perfectly fine?!

**Booting off the windows HDD will give me the error, i always boot off that drive and it normally brings up GRUB...at least it did for a day.

It is normal for windows to be installed on a NFTS partition and Linux to be installed on a Ext3 partition, i assume. (Different hard drives of course)

All help is greatly appreciated!:D

---

### Post by khamil8686 on 2010-01-07
64 bit gives you some extra speed and support for a ton of ram at no extra trouble except installing the ia32-libs package (***note i double checked the name and it seems its ia32-libs now not IA 32 like i thought) what id do is go home and install 9.10 over 9.04 and manually specify your partitions (i dont remember the exact wording but something similar to that, with a radio button!) then that should install grub 2 as the default bootloader and auto detect windows and things and add entries to the boot menu for ya and then you will be off and running :) i dont understand what you meant by it gives you the error when you boot off the windows hard drive, do you have all hard drives hooked up at the same time or do you switch between them like hot swappable (pluggable?) drives?
and yes windows is normal to be installed on an ntfs partition, ubuntu 9.10 will install on a ext4 partition which has some advancements above ext3 that i dont really know of, havent gotten to looking up the differences quite yet (or i looked them up and forgot :P i have a brain injury, so im like dory off the movie finding nemo, i have short term memory loss from a car accident)
i have a 80GB hard drive which has a 15GB windows ntfs partition and 60gb ext4 and a 5gb swap (i just heard you should have the same swap as you have ram but i never see my computer use any swap, just ram, so im not sure about that) i never use the windows partition, i just use windows for things like making themes for blackberry phones which i just installed windows in virtualbox in linux anyways, sorry im long-winded, i hope everything works smoothly for ya :)

-kyle

---

### Post by Buuntu on 2010-01-07
If Windows is the only hard drive installed in sda (your first hard drive), then there shouldn't be a grub menu in the first place.  Try booting off of the second drive in which you just reinstalled Ubuntu and seeing if that fixes the problem.

If you want to restore the Windows boot loader in the other HDD, you have to use your Windows 7 CD.  Instructions on how to do it with your Windows CD can be found here: [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html).

Also, posting the output of the following command (you can run it from a live CD) might be of use
```
sudo fdisk -l
```

---

### Post by Kdeeze on 2010-01-07
Yes, i have my first SATA hard drive that is 1 TB and has windows 7 on it. I have the second SATA hard drive that is 250 GB with ubuntu on it. Lastly, i have a 1TB hard drive for media files. And i also have a 1 TB external hard drive for media that is not plugged in. The other three are all internal and all plugged in. I also have a SATA BD reader/writer, along with 3 other optical drives installed.

When i had everything working i had the windows HDD set to boot first, but it still ran GRUB and let me choose which OS i wanted to boot from. I have 4 GB of ddr3 1600 RAM and a I5 processor and i like to back up HD media which would explain all my hard drives/reason for going to 64 bit. I am going to go home and install 9.10 over the 9.04 installation and hopefully it can be a little bit smarter.

I have tried to boot just from the windows HDD but it still wants to go into GRUB for some reason that i do not understand. I am guessing that GRUB doesn't recognize the two different boot locations, hopefully 9.10 will fix this. I will let yall know when i get home and install it. It will either be tonight or tomorrow afternoon depending if i go to my girlfriends after work or not.


> **Buuntu said:**
> If Windows is the only hard drive installed in sda (your first hard drive), then there shouldn't be a grub menu in the first place. Try booting off of the second drive in which you just reinstalled Ubuntu and seeing if that fixes the problem.

If you want to restore the Windows boot loader in the other HDD, you have to use your Windows 7 CD. Instructions on how to do it with your Windows CD can be found here: [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html).

Also, posting the output of the following command (you can run it from a live CD) might be of use
```
sudo fdisk -l
```


I will post the result of that command before and after i install 9.10 64bit as soon as i get access to my PC (asap)!

edit: will have that posted in about 2 hours.

---

### Post by Kdeeze on 2010-01-08
Here is the outcome of running ```
sudo fdisk -l
``` in my live boot of 32 bit ubuntu 9.04:


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xafb062d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60944   489428992    7  HPFS/NTFS
/dev/sda3           60944      121601   487227392    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ce8ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29275   235151406   83  Linux
/dev/sdb2           29276       30401     9044595    5  Extended
/dev/sdb5           29276       30401     9044563+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d2a4593

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976761528+  42  SFS

Disk /dev/sdh: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1         492     3948512+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 38 )
```

I wrapped the output in code tags, is this what people usually do? I am obviously new to these forums. I am now going to install my 64 bit version of ubuntu 9.10 and let yall know how it goes.

---

### Post by Kdeeze on 2010-01-08
Thanks to everyone that responded to this thread. GRUB worked successfully with my installation of ubuntu 9.10 - 64 bit. To compare, i am going to copy and paste the output of the same fdisk command in 'code tag'.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xafb062d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60944   489428992    7  HPFS/NTFS
/dev/sda3           60944      121601   487227392    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ce8ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29164   234259798+  83  Linux
/dev/sdb2           29165       30401     9936202+   5  Extended
/dev/sdb5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d2a4593

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976761528+  42  SFS

```



The only differences i see are the start and end time of my HDD with Ubuntu installed. I am clueless to these results. If anyone has some insight into what this means, go for it! :]

---

