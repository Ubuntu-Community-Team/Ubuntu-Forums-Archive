---
title: "Best procedure for clean install?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-11-18
Hi

I currently dual boot WinXP and Jaunty. I have 2 physical hard drives, one of which contains both OS's.

I want to wipe Jaunty and install Karmic.  As an initial test last night I stuck in a live CD, but when it came to the partition editor it said i had no other OS's on the machine...

What is the best way to go about this task?  Is it better to use a gparted live cd and go in and format the Jaunty partition, then let the Karmic live cd install on largest continous free space?

Any and all advice welcome.

---

### Post by arnab_das on 2009-11-18
this is a step by step pictorial guide for ubuntu 9.10 installation.

[http://thoughtsndreams.wordpress.com/2009/11/17/install-ubuntu/](http://thoughtsndreams.wordpress.com/2009/11/17/install-ubuntu/)

---

### Post by kimda on 2009-11-18
Why not upgrade jaunty to karmic instead of a clean install? 

If you want to wipe jaunty i would select custom when you get to the partitioning part. Then you can select the disk you want to use. Just select the partitions currently used by Jaunty and delete them. Be careful not to delete the fat/ntfs partitions with Windows on it. After deleting the partitions you can recreate them. I recommend going for a seperate /home partition so that in the future you can keep your home folders with new installs. My current setup is: /dev/sda1 - boot (/boot) partition ext3, /dev/sda5  - root (/) partition ext4, /dev/sda6 - home partition (/home), and /dev/sda7 swap - 2gb in my case. Make sure /boot and / are big enough (mine 250mb and 11gb).

---

### Post by arnab_das on 2009-11-18
> **kimda said:**
> Why not upgrade jaunty to karmic instead of a clean install? 

If you want to wipe jaunty i would select custom when you get to the partitioning part. Then you can select the disk you want to use. Just select the partitions currently used by Jaunty and delete them. Be careful not to delete the fat/ntfs partitions with Windows on it. After deleting the partitions you can recreate them. I recommend going for a seperate /home partition so that in the future you can keep your home folders with new installs. My current setup is: /dev/sda1 - boot (/boot) partition ext3, /dev/sda5  - root (/) partition ext4, /dev/sda6 - home partition (/home), and /dev/sda7 swap - 2gb in my case. Make sure /boot and / are big enough (mine 250mb and 11gb).

its an option but unfortunately didnt work for me when i tried :(

its better to go for a freash install, the filesystem is new in karmic also the GRUB version is newer.

---

### Post by aquascrotum on 2009-11-18
> **arnab_das said:**
> this is a step by step pictorial guide for ubuntu 9.10 installation.

[http://thoughtsndreams.wordpress.com/2009/11/17/install-ubuntu/](http://thoughtsndreams.wordpress.com/2009/11/17/install-ubuntu/)

This doesnt answer my question at all? I'm asking about the best way to remove my existing Jaunty and let Karmic find its own place.  I've already established that the LiveCD doesnt think there is an existing OS on my hard drive which clearly isnt the case.

> **kimda said:**
> Why not upgrade jaunty to karmic instead of a clean install? 


I upgraded Hardy to Jaunty and had a few problems.  All the Karmic horror stories seem to come out of upgrading. The consensus seems to be that a clean install is a happy install.  I have my home folder backed up and a list of my non standard apps so I'm happy enough to wipe and go with a fresh start.

---

### Post by arnab_das on 2009-11-18
its better to backup your data and go for a fresh install.

at least thats what my opinion is. upto u now.

---

### Post by philinux on 2009-11-18
> **aquascrotum said:**
> Hi

I currently dual boot WinXP and Jaunty. I have 2 physical hard drives, one of which contains both OS's.

I want to wipe Jaunty and install Karmic.  As an initial test last night I stuck in a live CD, but when it came to the partition editor it said i had no other OS's on the machine...

What is the best way to go about this task?  Is it better to use a gparted live cd and go in and format the Jaunty partition, then let the Karmic live cd install on largest continous free space?

Any and all advice welcome.

Boot the livecd and at the menu choose check cd for defects if you've not already done this. It should show your os's in the partitioner.

---

### Post by shababhsiddique on 2009-11-18
> **aquascrotum said:**
> Hi

I currently dual boot WinXP and Jaunty. I have 2 physical hard drives, one of which contains both OS's.

I want to wipe Jaunty and install Karmic.  As an initial test last night I stuck in a live CD, but when it came to the partition editor it said i had no other OS's on the machine...

What is the best way to go about this task?  Is it better to use a gparted live cd and go in and format the Jaunty partition, then let the Karmic live cd install on largest continous free space?

Any and all advice welcome.

wipe????  you meant it? backup the archive with APTonCD and then format both your / and swap partition of jaunty. If you think your XP will not boot after that then try backing it up with 'Hiren' its a good tool to play with. for problems with GRUB go to 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

