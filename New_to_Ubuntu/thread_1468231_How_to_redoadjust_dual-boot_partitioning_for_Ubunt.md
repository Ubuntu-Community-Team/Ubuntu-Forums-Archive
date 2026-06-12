---
title: "How to redo/adjust dual-boot partitioning for Ubuntu 10.04?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by resander on 2010-05-01
I want a dual-boot with Windows XP. The computer just came back from repair shop preinstalled with Windows XP. Disk size is 150GB and the repairshop partitioned the disk 50GB for XP and 100GB (as drive D:?). Before starting I could see a drive C: containing folders and files and a drive D: from Windows Explorer.

On installing Ubuntu 10.04 I selected 'side by side' installation and got this:

Partition      FileSystem   Size      Flags
/dev/sda1       ntfs        48.8GB    boot
/dev/sda2       extended   100.2GB   lba
  /dev/sda5     ntfs        50.4GB
  /dev/sda6     ext4        47.8GB 
  unallocated   unallocated  1.0MB
  /dev/sda7     linux-swap   2.1GB

I was hoping /dev/sda5 would go to Ubuntu resulting in 50GB for Windows XP and 100GB for Ubuntu, but now it is the opposite.

I don't mind reinstalling Ubuntu, but what I do next time when installer asks about the partitioning given the partitions above? If I have to select 'advanced partitioning' what are the steps? I have no experience in using gparted, so don't want to guess and get it wrong.

Would be grateful for assistance.

---

### Post by golanbatrac on 2010-05-01
Read this:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Your partition table should ultimately look something like this:

```

/dev/sda1   XP                    ntfs         50Gb
/dev/sda2                         extended
/dev/sda5                         linux-swap   3Gb
/dev/sda3   Ubuntu                ext4         10Gb   boot   /
/dev/sda4   Ubuntu Home           ext4         87Gb          /home

```You'll want to delete all of your current partitions except sda1 (the XP partition) and then set up sda2, then sda3, then sda4, and then set up sda5 within sda2.  You'll also want to allow the installer to overwrite the MBR when prompted to do so during installation.

---

### Post by resander on 2010-05-01
Many thanks Golanbatrac.
The document you referred me to is excellent.

I am now using gparted from the Live CD trying to delete partitions shown to the right of /dev/sda1. 

Q1.
When I select (=clickon) /dev/sda5 and click Delete the following error pops up:

```

  Unable to delete /dev/sda5!
  Please unmount any logical partitions
  having a number higher than 5

```

I assume partition number here is digit 5 in sda5, 6 in sda6.
I then selected /dev/sda6 hoping to find an Unmount 
menuitem. It was there, but inactive greyed-out.

When I try deleting /dev/sda6 a similar message pops up:
```

  Unable to delete /dev/sda6!
  Please unmount any logical partitions
  having a number higher than 6

```

The last linux-swap partition does not have an Unmount and the Delete menuitems is greyed out.
What do I need to do?

Q2.
If I manage to delete all partitions except /dev/sda1 using the Live CD and then start the installation, can I choose 'side-by-side' installation when the installer asks about partitioning? Will the installer then give all freed space to Ubuntu and the linux-stack automatically like a fresh install?


However, I will probably opt for the partitioning suggested by Golanbatrac.

Q3.
Is the rationale for having a /home partition to keep users, programs and data while reinstalling or upgrading without having to backup? 10GB is the suggested size for system programs and data. What is approximate size of this for 10.04? Is the unused part of it available to users?

Q4.
The boot flag is attached to the sda1 entry when I look at it now. It is moved to sda3. Why is this?

---

### Post by florus on 2010-05-01
I think your problem is that your swap partition is mounted. You must disable swap before you can proceed. Sorry I can't be more helpful, but I can't remember how to do it.
Golanbatrac's partitioning suggestion is spot on - go with it.

---

### Post by eriktheblu on 2010-05-01
/dev/sda1 ntfs 48.8GB boot
This is your C drive in Windows. This may be reduced depending on your software needs. Windows should run fine in under 20GB. 

/dev/sda5 ntfs 50.4GB
This is your D drive in Windows. With a partitioned disk, Windows will normally separate the user files and settings from the OS (like having a /home and / partition in Linux). You cannot delete this partition and still expect to use Windows.

If you want Windows to take up 50 GB and Ubuntu to have 100, first resize sda1 to 20 GB and sda5 to 30.

/dev/sda6 ext4 47.8GB
This is for Ubuntu, you can expand it later.

/dev/sda7 linux-swap 2.1GB
This is fine where it is, no need to mess with it.

---

### Post by eriktheblu on 2010-05-01
Step 1: back up all data.

Step 2: boot windows and clean up and defragment both partitions

Step 3: Boot a Live CD with Gparted, you can use the Ubuntu CD

Step 4: Resize sda1 (C:)

Step 5: Resize sda5 (D:)

step 6: Move sda5

step 7: Resize sda6

Recommendation: Leave some unformatted space between your partitions in case you need to expand later.

---

### Post by golanbatrac on 2010-05-01
> /dev/sda5 ntfs 50.4GB
This is your D drive in Windows. With a partitioned disk, Windows will normally separate the user files and settings from the OS (like having a /home and / partition in Linux). You cannot delete this partition and still expect to use Windows.This is true.  Short of reinstalling XP, you're probably stuck with the sda5 partition.  Defragging the hard drive is also excellent advice.

> Q1.
When I select (=clickon) /dev/sda5 and click Delete the following error pops up:

     Code:
       Unable to delete /dev/sda5!
  Please unmount any logical partitions
  having a number higher than 5 
I assume partition number here is digit 5 in sda5, 6 in sda6.
I then selected /dev/sda6 hoping to find an Unmount 
menuitem. It was there, but inactive greyed-out.

When I try deleting /dev/sda6 a similar message pops up:
     Code:
       Unable to delete /dev/sda6!
  Please unmount any logical partitions
  having a number higher than 6 
The last linux-swap partition does not have an Unmount and the Delete menuitems is greyed out.
What do I need to do?Old solution to, what sounds like, the same problem you're having:

> You are booting from the Live CD here, correct? If so, you may have run into a problem with Gparted on the Ubuntu 8.04 (at least) Live CD. Minimize the Gparted window, see if there is a "volume" mounted on the desktop; if there is, right click on the icon, select "Unmount Volume", when icon disappears, maximize the gparted window and right-click the partition.[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=829267](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=829267)


> Q2.
If I manage to delete all partitions except /dev/sda1 using the Live CD and then start the installation, can I choose 'side-by-side' installation when the installer asks about partitioning? Will the installer then give all freed space to Ubuntu and the linux-stack automatically like a fresh install?I've never tried the 'side-by-side' option.  If I had to guess, I'd say that it would give the remaining 100 Gbs to Ubuntu, but I don't know for sure.

> Q3.
Is the rationale for having a /home partition to keep users, programs and data while reinstalling or upgrading without having to backup?Exactly right.

> 10GB is the suggested size for system programs and data. What is approximate size of this for 10.04? Is the unused part of it available to users?I haven't installed Lucid yet, but normally it's 5 Gb or less on a fresh install.  But the amount of disk space it takes increases over time and as you install more programs.  Giving Ubuntu 10 Gbs means that it'll be a good long time before you need to prune.

> 
Q4.
The boot flag is attached to the sda1 entry when I look at it now. It is moved to sda3. Why is this? 

You'll be using grub2 as your bootloader.  Every time you boot you'll have the option to boot into either XP or Ubuntu.  Ubuntu will be the default if you don't choose one or the other.

---

### Post by oldfred on 2010-05-01
Gparted normally uses the existing swap if it finds one. The way to unmount it is to click on the swap partition and right click swapoff.

Linux does not use boot flags. Windows has to have a boot flag (active partition) as that is how the windows boot loader (and some others) find the partition to boot. Some BIOS seem to assume windows so will not let you boot anything unless you have a boot flag on a primary partition.

---

### Post by resander on 2010-05-02
Very useful responses! Many thanks!

Clearing the flag in linux-swap partition enabled me to delete the other partitions. I tried the side-by-side install option again. It ran to completion with no questions asked. BUT it extended the size of the XP partition from 50GB to 76GB, so Windows XP still has far more space than I want. 

Why? I deleted the D partition via gparted (not being aware that it might cause Windows XP to malfunction). 

Actually, Windows XP is still working. It has no programs other than the AVG virus scanner that I downloaded and added. The Defrag program reported there is no need to defrag drive C. 93% of the space is free and there is a massive amount of free space displayed (white colour) after the unmovable fragments.

I would like to try side-by-side installation once more to see if I can make it do what I want by reducing the size of the XP partition from gparted. 

When I understand this a bit better I will do the partitioning suggested by Golanbatrac.

---

### Post by oldfred on 2010-05-02
The automatic install tools are to make it easier for those who just want a basic install and do not understand partitions. I used just root & swap for 3 years with a shared NTFS data partition, but on upgrading to Karmic I moved /home to a separate partition and created data partitons.

If you want full control over partitions, you need to create them in advance with either the liveCD or separate download of a gparted liveCD. Then you can use manual install where you just choose which partition is root, what format, which partition is /home (and no format) and it finds swap on its own.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by resander on 2010-05-02
I made a second attempt to use side-by-side placement after having resized the XP partition to 30GB. I verified the partition was 30GB using the Windows Explorer before the install.

After re-installing Ubuntu the Windows partition had been extended to 76GB the same unwanted value as before. Am I making some mistake or is this the way side-by-side installation works? Has anybody else observed this? 

I am now trying to do the partitioning suggested by Golanbatrac and have defined the three partitions for root, home and linux-swap, but I don't know how to specify the two partition mount points (/ and /home) to gparted on the Live CD.

I am stuck and would be grateful for help.

---

### Post by oldfred on 2010-05-02
You can give labels to partitions in gparted but that is for your own use. 

You only assign partitions to / , /home or possibly others during manual install, not at gparted if you are running gparted from the liveCD.

---

### Post by resander on 2010-05-03
Many thanks oldfred,
I followed your advice and the partitioning suggested by Golanpatrac is now working.

I am still curious about the side-by-side partitioning. I observed the installer increasing the Windows partition size to about half the size of a 150GB disk. Would it use the same proportions for any size of disk? 

Those experienced in partitioning can use the tools to do exactly what they want quickly. For me it was an uphill struggle. I think there should be different off-the-shelf partitioning choices:

 - use entire disk for Ubuntu using root and home partitions
 - dual-boot with Windows using root and home partitions for Ubuntu
 - upgrade/change Ubuntu when using root and home partitions
    (to stop the user formatting the home partition by mistake)
 - manual/advanced as of now 
 
For the first three the user only makes the choice and the installer handles the rest.

I learned a lot from the responses in this thread.

Many thanks again.

---

### Post by butterthief on 2010-05-14
macbook 10.4.11
2.16ghz intel core 2 duo
1gb 667mhz ddr2 sdram

total beginner, have been reading about partitioning til my eyes have glazed over. would appreciate any suggestions for partition layouts.

i downloaded 'clonezilla' and ubuntu LiveCD, backed up my data, wrote zeros to the drive, installed fresh os x on a 40G partition, leaving 40G free space, then 40G for ubuntu. there seem to be several ways to order/format the partitions and am a bit lost. 

does this order/sizing make sense for my system?

primary partition: 40G os x
some free space in between...future flexibility for sizing
extended partition:
logical partition: 4G swap
logical partition: 40G /home
logical partition: 2G /boot
primary partition: 15G /root

my goals are twofold:
1. learn a new OS, so am starting with ubuntu.
2. learn how to back up/wipe/reinstall quickly, so if i mess something up, its not so catastrophic...makes it more fun to play...

it seems that some partitions need to be next to others or in a particular order. i appreciate any ideas or input, so thanks in advance for your help.

---

