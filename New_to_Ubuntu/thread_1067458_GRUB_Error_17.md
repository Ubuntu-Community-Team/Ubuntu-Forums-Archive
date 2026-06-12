---
title: "GRUB Error 17"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Indian_Guy101 on 2009-02-11
Ok lemme apologize to begin with because this has nothing to do with ubuntu. I set up a dual boot between freeDOS and DSL on one of my computers, took out the harddrive with the dualboot set up and working fine and put it into my 97 IBM Aptiva which has high enough specs to run all the software on the harddrive and I get error 17. I shecked the cable and the jumper connections aare proper any ideas?

---

### Post by leonardo_neo on 2009-02-11
View this link, and you will for sure get the solution for your problem...

> [http://ubuntuforums.org/showthread.php?t=1062971](http://ubuntuforums.org/showthread.php?t=1062971)

---

### Post by Indian_Guy101 on 2009-02-12
Wait so this is like a lice boot loader so I will have to use a floppy every single time that I start up? I ammconfused.

---

### Post by leonardo_neo on 2009-02-12
> **Indian_Guy101 said:**
> Wait so this is like a lice boot loader so I will have to use a floppy every single time that I start up? I ammconfused.

No you are not getting it. Study more about the super grub disk. Super Grub Disk help you to redirect your boot information, in this case GRUB menu. 

First, you need not necessarily have to use 'floppy'. Super Grub Disk works in CD as well as flash drive.

Second, it will help you to regain and redirect the boot information. You will be able to boot whichever OS you want to boot. You can boot both Linux, and Windows.

Third, you don't have to use this every time to boot the OS. Once you direct the boot information to the MBR, you are done.

There are some other ways to edit boot information in MBR, but this is a simple way I guess.

Hope this helps :)

---

### Post by stalkier on 2009-02-12
> **leonardo_neo said:**
> No you are not getting it. Study more about the super grub disk. Super Grub Disk help you to redirect your boot information, in this case GRUB menu. 

First, you need not necessarily have to use 'floppy'. Super Grub Disk works in CD as well as flash drive.

Second, it will help you to regain and redirect the boot information. You will be able to boot whichever OS you want to boot. You can boot both Linux, and Windows.

Third, you don't have to use this every time to boot the OS. Once you direct the boot information to the MBR, you are done.

There are some other ways to edit boot information in MBR, but this is a simple way I guess.

Hope this helps :)

+1 on Super Grub Disc. This is a very valuable tool. I used it this morning to correct my Error 17 on my drives.

---

### Post by Indian_Guy101 on 2009-02-13
> **leonardo_neo said:**
> No you are not getting it. Study more about the super grub disk. Super Grub Disk help you to redirect your boot information, in this case GRUB menu. 

First, you need not necessarily have to use 'floppy'. Super Grub Disk works in CD as well as flash drive.

Second, it will help you to regain and redirect the boot information. You will be able to boot whichever OS you want to boot. You can boot both Linux, and Windows.

Third, you don't have to use this every time to boot the OS. Once you direct the boot information to the MBR, you are done.

There are some other ways to edit boot information in MBR, but this is a simple way I guess.

Hope this helps :)
TY I am a beginner I prefer to use a floppy. how do I "direct the boot information to the MBR?" sorry if my question is stupid. I am a beginning programmer/hacker/linux user (I am only 12)Also will I have to reinstall the operating system(s) after doing this SUPER GRUB DISK THINGY?:lolflag:

---

