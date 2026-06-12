---
title: "I have Ubuntu installed on my laptop, and want to dual boot windows 7 with it..."
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Absolome on 2010-04-10
How do I go about doing so? I am completely new to ubuntu and practically need a guide that holds my hand throughout the whole dual boot process, I want to keep all of my ubuntu files, and of course all the guides I can find want me to install it starting with windows

---

### Post by LoloftheRings on 2010-04-10
It's indeed easiest and safest to start with windows. If you want to install windows last, you will have to make sure Windows installs on the right partition (can be confusing sometimes) and you will have to recover ubuntu's bootloader.

Unless you really want to do this (it's possible, but you'll have to take some time to do it), its best to make a backup of your current files and install windows first.

---

### Post by spiky001 on 2010-04-10
+1 windows 1st, or you will have to learn abit

---

### Post by Absolome on 2010-04-10
Also, if I have to install windows first, I have a flashdrive windows 7 loader, how do I go about doing so, I can't install it on the main partition because it's not NTFS

I am really no good at this kind of stuff, and I have a feeling even if I worked on backing them up I'm going to lose the work I've put into ubuntu (mainly in finding the damn drivers for graphics and wireless)

---

### Post by norm7446 on 2010-04-10
Your problem here is Windows. It likes, sorry it will only work if it is in the first part of the primary partition. Linux on the other hand will work anywhere on the primary partition. so if you want to dual boot, you must first install Windows. Then defrag it to settle it all near the front of the primary partition, then and only then can you install Ubnutu. Long way round for a short cut I know but this is the only way to cause you the least prob's later with a dual boot of Windows and Linux. Blame Uncle Bill and his mate's for this.

---

### Post by Absolome on 2010-04-10
Yes, but how do I install windows if the primary partition isn't NTFS?

how do I convert it so that I can use my USB loader to insall it?

---

### Post by spiky001 on 2010-04-10
the boot loader should let you reformat the drive then make a partion the siz you want for windows

---

### Post by oldfred on 2010-04-10
You can have 4 primary partitions or 3 primary and one extended with many logical partitions inside the extended.
Windows can be installed to any primary partition not necessarily the first.
What partitions have you used?
```
sudo fdisk -l
```

---

### Post by norm7446 on 2010-04-10
Ok. First you will need to reformat the H/Drive to either Fat32 or NTFS for Windows to install onto. If your Windows disc does not recognize the H/Drive. You will have to do it another way first. What I usually use is the Ultimate Boot disc ( check the download link below and burn it to a CD. I would recommend K3B, but you could use any burning software you like as long as it supports ISO9660 files ). Set your system to boot from the Cd Rom and boot the Ultimate Boot Disc, in the Installation section you will find a myriad of Partition software, that will repartition the H/Drive to either Fat32 or NTFS. Once you have done this you can then, restart the system and install Windows.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by Absolome on 2010-04-10
I have just one more quick question, is there any way to backup my wireless driver? I had to jump through a bunch of hoops for it and really don't want to have to do that again

---

### Post by spiky001 on 2010-04-10
I dont think you can save them if i,m wrong some1 will put me right, but think of what you will learn as this is all a new experiance

---

### Post by Absolome on 2010-04-10
ok, so I just tried again, windows installer does not change the partition's file format ro NTFS, it just tells me it can't install because the partition is on an unrecognized file system

please help me out here

---

### Post by spiky001 on 2010-04-10
ok have a look at what norm posted on 1st page

---

### Post by oldfred on 2010-04-10
several install windows after Ubuntu. If the site is older the only real change is for the instructions to reinstall grub should change to reinstalling grub2. The difference between the versions of windows also is not significant.

[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

Use these instruction to restore grub2 after the install:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

