---
title: "Fresh Ubuntu Install"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by bandelguy on 2011-03-01
I am currently using Windows 7 and I have tested the Ubuntu through the live version and liked the OS overall.

I have 3 drives containing: 
C: Windows and programs
D: Movies, music and photos.
E: Misc.files
I wish to make my Ubuntu installation as - 
Partition 1: Ubuntu
Partition 2: Movies, Music and photos.
Partition 3: Misc files.
I have some questions: 
1. How can i Install Ubuntu so as to keep media and misc files (documents, etc) in separate drives as above?
2. Whether I have to mount the other 2 drives so as to access the files in the other drives?

I wish to go for fresh install on 160GB Hard Disk.

Please guide in the installation and formatting the disk.

---

### Post by mastablasta on 2011-03-01
are you planning to format the disk (remove win7)?
 
If so then during install you will decide on partition for root (/) and then a separate one for home (/home) and anothe rone for /swap (probably 2 GB). 
 
all configuration files will be put in home. usually this is also where you save files from user. think of it as My documents in windows. sort of. 
 
i am not sure why you need a separate partition for misc files.
 
 
but you should know that you can partition you drive later if you find the need for that. so you could just let it partition automaticly first and then mount home as separate partition. In linux partition are like folders and devices like files and folders :-) well not exactly but this helps me understand it.
 
partitions are mounted automaticly by nautilus when you try to access files on them. 
 
also have a look at ubuntu manual to learn a bit more about system instalation.

---

### Post by Elaztic on 2011-03-01
When you install go for manual partitioning.

In the partition that contains the windows OS you create:
/swap (preferably the size of your RAM)
/ (the root directory for Ubuntu OS files 8-10 Gb is more than enough...if you are running out of space then go for ie. 5 Gb)
/home (which is for configuration files, documents (if other partitions are not used for this) and everything else)

If you want to keep your other partitions intact then just don't touch them. Ubuntu can easily read and write to the existing windows NTFS file system.

---

### Post by bandelguy on 2011-03-02
As said in the first post, I wish to replace the Win 7 with Ubuntu as my main OS. 
Deleting the C drive(30gb) and thereby, creating a free space in the drive,I can install Ubuntu. Is this a good and correct way to install? What file system and how much space should I use and Mount point for /swap, / root, /home ?

---

### Post by harkumar on 2011-03-02
> **Elaztic said:**
> When you install go for manual partitioning.

In the partition that contains the windows OS you create:
/swap (preferably the size of your RAM)
/ (the root directory for Ubuntu OS files 8-10 Gb is more than enough...if you are running out of space then go for ie. 5 Gb)
/home (which is for configuration files, documents (if other partitions are not used for this) and everything else)

If you want to keep your other partitions intact then just don't touch them. Ubuntu can easily read and write to the existing windows NTFS file system.

its very much clear from the above,
/root will be the first part of your 30gb
/home will be the 2nd part and
/swap is the last part

creating sequence is **/root** then** /swap **and then** /home**

good luck and enjoy ubuntu.

---

### Post by mastablasta on 2011-03-02
it's a correct weay to install. you will have more than enough space for it and additional applications. use ext3 or ext4 (i use ext4)
 
Ubuntu can also autopartition that part empty of disk, so you don't have to worry about those things ;-)
 
If you just deleted the partition you could use largest free space. but someone here will hopefuilly confirm if this function works propperly in 10.10. I knwo it does in 10.04.

---

### Post by harkumar on 2011-03-02
yes it works perfectly with 10.10.

---

