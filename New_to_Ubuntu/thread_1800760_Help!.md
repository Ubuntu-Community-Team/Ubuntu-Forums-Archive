---
title: "Help!"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by xcalirish on 2011-07-09
Hi, I have ubuntu running through wubi in the windows partition.  my ubuntu drive is full.  I have run the clean command in an attempt to free up space.  everything I have tried to free up space has failed.  I am leery about playing with the partition size with gparted on the install disk i have.  I have burned everything i need from windows but cannot access ubuntu through the os gui, only through terminal.  I really just need to retrieve some photos and docs before wiping the drive and doing a full ubuntu install.  I have tried the solutions i have found in the forums and nothing has been successful.  I am not sure what to do next.

---

### Post by matt_symes on 2011-07-09
Hi

Manually mount an external hard drive and copy the photo's onto there. You could also burn the photos onto a cd or dvd using the wodim command from the command line. If you are unsure how to do this post back.

You can check the disc usage from the command line using

```
sudo du -h / | sort -nr | head -n 30
```Enter your password. It will not be echoed to the screen. 

This will give you the 30 largest files and folders on the drive. Then you can delete anything you don't need.

Kind regards

---

### Post by conradin on 2011-07-09
I dont think wubi sets up a partition on your HD. not by default atleast.
Ihavent used Wubi in several years, but Last i recall it set up in a folder in your windows filesystem. That said, what you would be modifying in windows is a file. Wubi thinks this virual filesystem is a whole new partition... anyways, I dont think it particularly risky to resize a virtual filesytem. How much disk space do you have (entirely / on the wubi install?)


This link might help you:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
also have a look at:
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by Rubi1200 on 2011-07-09
Hi and welcome to the forums xcalirish :)

First, do not try and resize the Wubi root.disk with GParted; it is a recipe for disaster!

You can follow the advice posted by Matt and save your files or mount the root.disk from a LiveCD and access them that way:

```
sudo mkdir /media/win  
sudo mount /dev/sda1 /media/win 
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```
This example assumes that sda1 is the Windows/Wubi partition; change to reflect your actual situation.

If you want to resize the root.disk, post the output of df -H from the Wubi install so we can see what the original size was designated as.

You also have the option to create a partition on the disk and migrate the Wubi install to it:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by xcalirish on 2011-07-09
Thanks Matt, I would like to burn the photos.  I am unfamiliar with the wodim command.  I think the photo files are in the fspot directory.  I am not sure how to get there, precisely,  I am not versed enough on command line syntax.  Can you direct me?  Grateful for the help thanx

---

### Post by xcalirish on 2011-07-09
Thank you Rubi, My ultimate goal is to retrieve and burn photos from the fspot directory prior to reloading the machine solely with ubuntu.

---

### Post by matt_symes on 2011-07-09
Hi

The default directory for imported fspot pictures is called Photos (case sensitive) and i believe it's in your home directory (assuming you did not change the defaults).

```
cd ~/Photos
```

That will move you to the Photos directory in your home directory. You can then tar or zip (archive or compress) them up (if you want) and burn them.

```
man wodim
```

and 

```
man tar
```

and ```
man zip
```

Will display the manual pages for tar, wodim and zip. If you need more help then post back.

Kind regards

---

### Post by xcalirish on 2011-07-09
Thanks Matt, unfortunately since I am out of disk space I am having trouble getting anything to work. I think I would just want to copy the files to a flash at this point, I am not sure how to identify the flash drive or the command syntax to copy over to it.  Sorry to be such  a PITA.

---

### Post by wildmanne39 on 2011-07-09
> **xcalirish said:**
> Thanks Matt, unfortunately since I am out of disk space I am having trouble getting anything to work.I am not sure how to identify the flash drive or the command syntax to copy over to it.  Sorry to be such  a PITA.Hi, here is a guide for resizing the wubi partiton but first post the information that Rubi asked for because he is well versed in wubi installations.
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by matt_symes on 2011-07-09
Hi

> I am not sure how to identify the flash drive or the command syntax to copy over to it.You are trying to copy to a flash drive ? Maybe you don't have enough space to use wodim.

Anyway, To do that you need to follow Rubi's instructions.

At the console type

```
sudo fdisk -l
```Enter your password. It will not be echoed top the screen. That is a small L above. That will list all your drives like this.
```

matthew@matthew-laptop:/proc/acpi/thermal_zone$ sudo fdisk -l
[sudo] password for matthew: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d0c8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48827392   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        6079        7295     9765616   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3            7295        8511     9765888   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4858adf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
matthew@matthew-laptop:/proc/acpi/thermal_zone$ 
```Plug in the flash drive and type the same command again. The extra drive that has appeared is the flash drive.

Make a directory under /media
[FONT=monospace]
[/FONT]```
sudo mkdir /media/win   
```Change the ownership of the mount point.

```
sudo chown <user_name>:<user_name> /media/win

```

Change <user_name> to your user name.

Mount the drive.

```
sudo mount /dev/sdXY /media/win
```Where sdXY is the value returned from sudo fdisk command above (in my case /dev/sdb1). You might need to add the filesystem type. 

Copy the files across

```
cp /home/<user_name>/Photos/* /media/win
```Change <user_name> to your user name.

Kind regards

---

### Post by xcalirish on 2011-07-10
Matt and Rubi, I bow to your greatness!  Thank you it worked perfectly!  You guys are the best! I appreciate you putting up with my noob angst!:)

---

### Post by Rubi1200 on 2011-07-10
> **xcalirish said:**
> Matt and Rubi, I bow to your greatness!  Thank you it worked perfectly!  You guys are the best! I appreciate you putting up with my noob angst!:)
No problem, you are more than welcome :-)

I am sure Matt will also be pleased you got this sorted out.

If all issues are resolved, please mark this Solved using the Thread Tools near the top of the page.

---

