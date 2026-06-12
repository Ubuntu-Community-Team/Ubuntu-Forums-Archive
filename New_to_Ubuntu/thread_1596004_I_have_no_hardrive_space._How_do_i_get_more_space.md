---
title: "I have no hardrive space. How do i get more space?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Uruk-hai on 2010-10-13
I already have my c: drive mounted. But I cant figure out how to use it. I can get all of my normal files and stuff through the drive but when i try and move them to ubuntu it says that i only have like 400 mb's left?

---

### Post by drs305 on 2010-10-13
Do you know why you only have 400MB left? 

If not, it's often undeleted trash (including root's), large log files, or a backup that was supposed to be saved to another partition but wound up on the system partition. As a hint for troubleshooting, unmount all partitions except the / partition when trying to figure out what's gone wrong.

You can check out this thread on troubleshooting disk space issues:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

If you find you need to expand your system partition, this guide can help:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")
Also check out *srs5694's* link in that post's links section.

---

### Post by jtarin on 2010-10-13
Post the results from the comand in a terminal of ```
sudo fdisk -l
```Are you using WUBI installation?

---

### Post by Uruk-hai on 2010-10-13
Well. I'm not really sure how much. Only that its a very small ammount. But every time it tells me it has 2 options. Empty the trash or go to disk usage. Every time I want to move a movie from the c drive to my ubuntu desktop It says I dont have enough space.

I didn't use WUBI Installation by the way. 
Thanks for helping me guys. I'm super new at this.

---

### Post by Uruk-hai on 2010-10-14
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       59527   478110465    7  HPFS/NTFS
/dev/sda3           59528       60802    10235905    5  Extended
/dev/sda5           60742       60802      484352   82  Linux swap / Solaris
/dev/sda6           59528       60741     9750528   83  Linux

Partition table entries are not in disk order

---

### Post by jtarin on 2010-10-14
You have allowed almost the bare minimum for an Ubuntun install....with practically no room for data files such as movies.etc. I would have made a shared partition between Windows and Ubuntu to store such large files and the you could have used them from there.
While it is possible to [resize your Windows partition ]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")and make Ubuntu partition larger it is best to do this before installing Ubuntu. Doing after can be a very complicated process for someone new to Linux and partitoning. You should read this in its entirety before proceeding if you so choose. Be warned that you should have recovery disk for Windows before attempting.Search the forums for successful resizing exercises and not so successful. This is a matter that should be planned ahead before installing any Operating System. This is how we all learn.

[Other sources]("http://www.google.com/#hl=en&q=gparted+ubuntu+10.04+resize+windows+after+linux+installation&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=25d4dc8e37640127")

---

### Post by amjjawad on 2010-10-14
If you want to resize your Windows Partition then:

1- Make sure to backup ALL your files in Windows. If you have an external HDD, that would be your best option. Otherwise, DVDs will always be another option.

2- Never resize your Windows Partition unless you:
a) Delete all the temp files, cookies, etc ([http://www.piriform.com/](http://www.piriform.com/))
b) Defragment your Windows Partition

3- Always have rescue CD/DVD or any other media just in case something will go wrong.

4- If you're going to use GParted to resize Windows Partition, make sure to restart your machine after you do that. DO NOT do any other operation after the resize/shrink process, just reboot directly. I've lost my Windows Partition because I've done 2 more things after resizing my partition.

Good luck!

---

