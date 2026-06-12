---
title: "Need Advice about partitioning"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by Kavkaz86 on 2011-03-26
Hello.

I am using a netbook with 250 GB hard-drive which comes with stock 10.00 GB Windows 7 Starter loader, 2 GB Windows Vista Loader which are non-accessible (unless formatted). I also have 2 additional partitions: A windows 7 partition which contains all the windows files and a second partition for music and general data.

My question is: - for a healthy linux installation. how many partitions do I need and what type of partitions would they be? (I am planning to dedicate a 100 GB out of my 250 GB to linux so let's go with that)

Thank you,

---

### Post by MrEgg on 2011-03-26
I'd suggest 3 :

/ : 20 Gb max., type ext4 - you'll be more than comfortable with that
/home : 80 Gb type ext4, minus swap size
swap : same as your ram, type swap

---

### Post by Bucky Ball on 2011-03-26
MrEgg pretty much has it. All I could add is with the /swap, 2Gb is fine, double the size of your RAM if you intend hibernation. 

/ (root partitions; where your OS goes) and /home (your settings and personal data; it contains folders by default not unlike Windows eg /music /video /documents etc) are a good start but you can add whatever partitions you like - /recipes, /study, /sockinventory - whatever. Good luck with it. ;)

---

### Post by oldfred on 2011-03-26
+1 on MrEgg's suggestions

If you have used all 4 primary partitions you have to decide how to repartition as one has to be converted to the extended partition to hold the logical partitions you need for Ubuntu.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
The Hedge show grahically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by srs5694 on 2011-03-26
One more caution: *Do not use Windows tools to add more partitions!!*

Based on reports I've read here, it seems that recent versions of Windows, when asked to add partitions to a disk that already has four primary partitions, convert all the partitions into "dynamic" partitions. These use a proprietary Microsoft scheme that's similar to the Linux logical volume manager (LVM) system. The trouble is that nothing but Windows will be able to fully use or manipulate these partitions, so you'll have to undo this conversion to install Linux.

Another issue is that Linux resizing tools sometimes render a Windows boot partition unbootable.

Thus, if you need to add partitions for Linux, you should resize the Windows boot partition (if necessary) with the Windows partitioner, but do *not* add partitions using that tool. Instead, use GParted in Linux to create an extended partition and place new logical partitions in it. If you've already got four partitions, you'll have to either delete one or convert one into a logical partition. Oldfred's links should be helpful in dealing with such situations. In some cases, my [FixParts](http://www.rodsbooks.com/fixparts/) program can be helpful, since it can convert partitions from primary to logical form, at least under certain conditions.

---

### Post by Bucky Ball on 2011-03-26
Just make the 100Gb free space then create an extended partition with the free space with Gparted. Job done. Then create the partition inside that via manual partitioning when you are installing Ubuntu.

Ubuntu will survive fine in a logical partition, unlike Windows which needs to be on a primary (preferably partition 1, disk 1).

---

