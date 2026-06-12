---
title: "Boot files on backup disk"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by DC80 on 2010-04-22
Hi all, 

I have a problem with installing ubuntu. I even don't see Grub loading. Here is the thing. 

I have 2 hard drives, hdd 1 is 500 Gb (ubuntu) and hdd is 1000 Gb (using for backup). Now when i start my computer it is trying to load Windows 7, which i want to get rid of but without having my backup disk formatted. Is there any way to remove those windows 7 boot files and getting ubuntu installed?

I already have tried to use Bart's PE disk, this didn't help. I'm gonna try to disable my backup disk and install ubuntu again. I will be back after a while.

Thanks in advance.

DC80

---

### Post by ttshivers on 2010-04-22
yea.  Just remove your backup disk and tell Ubuntu to take up the entire hard drive in the installation.

---

### Post by DC80 on 2010-04-22
Didn't i tell that the drive is not to format? Otherwise i will lose my data! But thanks for the answer anyway.

@all: i will try to use a jumper so it will be in "slave" mode. Maybe then i will be able to remove the bootfiles from the drive.

---

### Post by ttshivers on 2010-04-22
Sorry on the ambiguity on my reply.  Just remove your backup drive from your computer, not remove all the files from it.  Then install Ubuntu and after Ubuntu is installed, then insert you backup disk.  If you do it that way then Ubuntu will not ever touch your backup drive.

---

### Post by DC80 on 2010-04-23
Well, that is not the problem. The problem is that Windows 7 has boot files placed on my backup disk. So when i start my computer it want to start Windows 7 instead of ubuntu. Grub isn't even loading. 

For now, i have a jumper in place so the disk is in "slave" mode. I will now try to mount the disk and remove all of windows 7 boot files.

Thanks for your reply.

DC80

---

### Post by DC80 on 2010-04-23
I have done it! I mounted the disk and removed the Windows 7 boot files (bootsect.dat, bootmgr and so on). Now i should have no problems at all. 

Thanks for the help. 

Here is how i have done it.

1. Place a jumper on the harddisk in question. The jumper will place the harddisk in "slave" mode.
2. Start your computer and boot into ubuntu.
3. Go to: System ==> Management (or so i think because i'm not english) ==> Disk utility and start the program.
4. Mount the disk by selecting it and click on the mount icon in the top left corner. When the drive is mounted a icon will appear on your desktop.
5. Access the drive by clicking on it and do what you need to do with it.

---

