---
title: "Unable to Install ubuntu"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Kushagra.19 on 2011-07-28
I have created a partition on my HP notebook with Windows on it. First the whole HDD is of Primary Partition type but after creating it into two , all the partitions became Simple Volume type. Moreover when i deleted the second partition and left it as in allocated space and tried to install ubuntu 10.04 LTS it simply says that unallocated space is unusable .

Please help me out .

---

### Post by Mark Phelps on 2011-07-29
Need more details ...

Are you running Win7?

How many partitions did you have on your drive originally?  You did say they were all primary.

Did you shrink an existing Win7 partition to make room? If so, was it your OS partition?  What tool did you use to do the shrinkage -- Win7 Disk Management or GParted?

Or did you remove an existing partition to make room? If so, which partition?

If it IS Win7, please go into the Win7 Disk Management utility, write down the information there about the partitions and post that back here.

Also, if you can boot from an Ubuntu LiveCD, do that, select the Try option, when you get to the desktop, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one). That will list off the partitions on your drive.  Then, post the results of that command back here.

---

### Post by scorchgeek on 2011-07-30
You need to create a new partition in that unallocated space before you can install anything. Creating a partition should be an option right in the installer.

---

### Post by Kushagra.19 on 2011-08-01
Yes i m running windows 7

Originally there was only 1 partition and from that partition only i have created an extra partition. The original partition is primary.

Original partition contains the Win 7 files.

I've used win disk management for creating the partition.


The result of the command  "sudo fdisk -lu" is :



Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x078c2322

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   976558079   488074240   42  SFS
/dev/sda4       976560128   976771119      105496   42  SFS

Disk /dev/sdb: 8011 MB, 8011087872 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008d3b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15635593     7817766    b  W95 FAT32
custom@custom:~$ ^C
custom@custom:~$






I am adding an image attachment which describe the information of the partitions.

---

### Post by westie457 on 2011-08-01
Hello 
     This is what I would do and your choice is to agree or disagree.

1 Boot into Windows and Defrag the C:\ drive at least twice to force Windows into as small a space as possible.

2 Go to disc management and shrink C:\ by as much as Windows allows. Remember that windows is greedy and wants more space than it needs. Leave the free space unallocated for now. 

3 Boot into a Live desktop and run Gparted. In Gparted select the Windows and then move/resize. Shrink this by as much as you want but leaving Windows with enough space. Click okay and Apply. You will now have a lot of free space (unallocated). Again leave this as it is for now.

4 Reboot into Windows. It should immediately tell you your hard drive needs to be checked for errors. Allow this to go ahead  and let it finish (better to do this now than later when real problems can occur). And let it finish booting.

5 Restart the computer into the LiveCD and select install. Set a few options relevant to your location and at the where to install screen select something else. You are choosing where to install.

6 In the partitioning window Select the unallocated space choose how large you want his to be; 25000-30000 MB is a good size _25-30GB).Click the first box and select EXT4, then mark the little box to format and then click Use As, select /.

7 Repeat step 6 selecting the remaining space (apart from a size that is equal to the amount of RAM in your computer. This small partition will be your Swap) using this as an EXT4 partition called /home. Remember to mark format.

8 At the bottom of this window is a section for where to install Grub. Make sure Grub goes to the MBR of the drive (the manufacturers name will be here correctly identifying the hard drive.

9 Click Finish and then Apply. The Install goes ahead. If any windows open for where to install Grub you can now accept the defaults.

10 Reboot into your dual-booting computer.

If I have missed anything or someone has other suggestions feel free to join in.

---

### Post by varunendra on 2011-08-01
If the image you attached shows current status, you don't have any extra partition at all! Almost all of it is occupied by the C drive.

Please boot from Ubuntu LiveCD, run Gparted and post its screenshot (press 'PrintScreen' key on the keyboard). It'll be much more easier to interpret for most of us. I'm not good at understanding fdisk outputs.. ;)

Besides, if you haven't already done it, please create Windows backup DVDs since you may require Gparted to resize the partitions, and it may corrupt your windows booting (although it is very unlikely with the apparent partition layout of yours).


**EDIT:**
Hmm.. I'm late again :D
Westie has suggested almost an excellent stepwise procedure to follow, just a few things to add up-
1) make sure to backup win7 first as sometimes, using gparted to resize win7 boot partition causes corruption in win booting.
2) make sure to first create an 'extended' partition in the unallocated space, because there is a limit of max. four primary partitions in a hard disk (extended one is counted as 'one primary partition').
3) create the new 'logical' partitions inside this extended partition.

@westie457,
is there a specific reason why you prefer a separate /home partition? I prefer one big partition (30-60 GB) for '/', one swap (2-2.5 GB, even with 4GB+ RAM as I don't use hibernation) and a separate, independent partition for user data.

---

### Post by westie457 on 2011-08-01
> @westie457,
is there a specific reason why you prefer a separate /home partition? I prefer one big partition (30-60 GB) for '/', one swap (2-2.5 GB, even with 4GB+ RAM as I don't use hibernation) and a separate, independent partition for user data.

Personally I don't have a separate /home, however like you I do have a huge shared partition for personal files. The recommendation is basically what others here with vastly more knowledge than me keep posting. While not strictly necessary to have the /home it is a good thing to have just in case when upgrading you accidentally format for the upgrade and end up with a clean install.

---

### Post by varunendra on 2011-08-01
> **westie457 said:**
> Personally I don't have a separate /home, however like you I do have a huge shared partition for personal files. The recommendation is basically what others here with vastly more knowledge than me keep posting. While not strictly necessary to have the /home it is a good thing to have just in case when upgrading you accidentally format for the upgrade and end up with a clean install.I think it depends upon what kind of setup a user is going to have and what his priorities are. And talking about 'people with vast knowledge', what do you think about oldfred? :)
I don't think I can explain the 'dependability' thing any better-
> **oldfred said:**
> ....
....
I do not believe in sharing /home either. Some do it and if the verisons  are all the same it will mostly work. If upgrading from one version to  another it is fine for the new verision will update settings. But if you  have systems using different versions of software you may get  conflicts. My /home is only about 1GB of mostly hidden folders &  settings as all my data is in a /data partition (including firefox &  thunderbird profiles and some other (normally) hidden data folders). 

I do believe in creating a /data partition and moving all your data  folders to that partition if you have multiple systems. Then you have no  conflicts and can easily mount your data in each system. I use linking  after mounting it.
Before reading this post, I also considered the separate /home thing as 'good for all'. But being deeply convinced with this explanation, I've been just quoting him ever since. It seems that there are very few 'general' rules in linux. Mostly they are dependent on several factors. But I think it's good. It is what makes linux different and better.

---

### Post by Hakunka-Matata on 2011-08-02
The[COLOR=Red] [SIZE=3]image  you attached in post#4[/SIZE][/COLOR] shows the drive to be a [SIZE=3][COLOR=Red]dynamic[/COLOR][/SIZE] volume.   The drive must be converted back to a [SIZE=3][COLOR=Red]basic[/COLOR][/SIZE] volume before you can install Ubuntu. See link below. Once you get the drive converted back to a basic volume boot to the Ubuntu LiveCD and use the "Gnome Partition Manager" Gparted to create your partitions.  You will need to create one Extended partition, after which you create one Ext4 Logical partition (40-50 GB is enough)for your Ubuntu system partition, /  and also one linux swap logical partition equal in size to the amount of RAM memory in your computer.  After that you should be able to install Ubuntu to the Ext4 partition.
 Check post #13 in this thread.  [http://ubuntuforums.org/showthread.php?t=1813172&highlight=dynamic+volume](http://ubuntuforums.org/showthread.php?t=1813172&highlight=dynamic+volume)  Converting the drive back to a basic volume is not a 2 minute job.

---

### Post by EkuquoL on 2011-08-02
... Windows doesn't like sharing partitions...

Automatically, Windows will allocate freespace.
It will appear as a different drive but Windows will still account it.
But when you ever use try to dual partition with Windows...

During the setup of Windows 7 -- XP you want to partition off the Windows into its own partition. Keeping at least half of the disk unallocated. 
After Windows is installed you will be able to  use that unallocated space as the Linux / Ubuntu partition.

An easier way to do that ... Using the diskTool on Ubuntu -- you can format freespace/empty space on the drive... Keep it unallocated and then install your Microsoft Xp/ 7 on it.

Another way to do it is find a VM client for windows... Which is just a small format tool to format freespace for use.

---

### Post by Mark Phelps on 2011-08-02
Did you try to FORCE the creation of a new partition -- when you already had the limit of four?  THAT will automatically convert your basic volumes to dynamic volumes.

Note that if you are able to convert back to basic volumes, you will STILL have the limit of four primary partitions.

Shrinking will do you no good because that is the maximum number of primary partitions you can have on one drive.  You will have to look at your partitions and decide which one you want to remove, and create a new Extended partition in it's place.

Also, do NOT, repeat NOT, use the Ubuntu installer or GParted to shrink Win7 OS volumes.  Doing so risks corrupting Win7 and rendering it unbootable.

---

