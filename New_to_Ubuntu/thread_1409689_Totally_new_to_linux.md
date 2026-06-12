---
title: "Totally new to linux"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by akshay_ on 2010-02-17
Hi guys,
       Like the subject line says I am totally new to linux. I want to install linux on my external hard drive so that I can boot up my laptop anytime on linux anytime. The file system on it is FAT 32. My laptop is running on Windows Vista with the file system of NTFS. Ok so my real question is, can I install linux on my external hard drive without losing the data that I already have on it. I have download the linux file from ubuntu website and burned it to a CD. How do I go about partitioning the hard drive if needed? Your help will be greatly appreciated.
Thanks,
Akshay

---

### Post by ubunterooster on 2010-02-17
during the install yo get the option to resize your exsiting partition. it is generally simple but...ALWAYS BACKUP ALL DATA AND HAVE WINDOWS RECOVERY DISCS just in case

---

### Post by louieb on 2010-02-17
The most common mistake made when installing on an external drive - is allowing GRUB to do the default install. The end result is the computer cannot boot without the external drive plugged in.  

You can change were GRUB is installed by pressing the advanced button on the install summary page. If you laptop only has 1 hdd the you would want to install GRUB on /dev/sdb. Then when you want to boot Ubuntu you will have to tell BIOS to boot the external drive. Otherwise it will boot as it currently does.

---

### Post by lindsay7 on 2010-02-18
Load the install disk and do not install it yet.  Look at the menu bar on the top of the screen and to to system/administration/ and then look for Gparted or partition manager (it is the same program) you can use this to partition you external drive as you would like it.

You can then do the install as you like.

---

### Post by Rayve on 2010-02-18
If I'm not mistaken, you will need to format the drive to ext3 (or ext4, if you'd like, and are using Karmic) filesystem, rather than FAT32 it is now.  That means you'll lose all data on that partition, and if you make it the entire external drive, you will lose all data on that drive.

Even if you only do a partition and leave part of it FAT32, it's always a good idea to backup your data, especially before you change any partitions.

Once you have an ext3/ext4 partition/entire external drive, you can then install Linux.  The other posters above have mentioned editing the way GRUB loads since it will be on an external drive.

If you need anything else, the documents at [https://help.ubuntu.com/](https://help.ubuntu.com/) will be helpful, as will folks on the forums here.  :)  Good luck!

---

### Post by bilalakhtar on 2010-02-18
> **Rayve said:**
> If I'm not mistaken, you will need to format the drive to ext3 (or ext4, if you'd like, and are using Karmic) filesystem, rather than FAT32 it is now.  That means you'll lose all data on that partition, and if you make it the entire external drive, you will lose all data on that drive.

Even if you only do a partition and leave part of it FAT32, it's always a good idea to backup your data, especially before you change any partitions.

Once you have an ext3/ext4 partition/entire external drive, you can then install Linux.  The other posters above have mentioned editing the way GRUB loads since it will be on an external drive.

If you need anything else, the documents at [https://help.ubuntu.com/](https://help.ubuntu.com/) will be helpful, as will folks on the forums here.  :)  Good luck!

Exactly. You will have to format your external HDD in the ext3/ext4 file system. You can format only a part of it by shrinking the existing FAT32 partition and formatting the free space with ext3/4. You can use GParted for all this. To use Gparted, boot using the install cd (but DO NOT SELECT TO INSTALL IT, instead select "try ubuntu without any change to the computer") and when the system boots, select system->administration->gparted partition manager in the top menu.:popcorn:

---

