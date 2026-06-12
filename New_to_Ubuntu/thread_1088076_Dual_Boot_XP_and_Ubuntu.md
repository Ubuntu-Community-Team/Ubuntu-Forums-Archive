---
title: "Dual Boot XP and Ubuntu"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by aadil23 on 2009-03-05
I have been using windows forever but i am tired of it plus i am very eager to learn more about Linux and Ubuntu. 
I have Windows XP SP3 installed on my laptop and i tried out Ubuntu using virtual box. Now i want to install Ubuntu so i can run it without going into windows. My n00b questions are:
1. Will i need to to a fresh/complete installation of Windows Once again before i install Ubuntu as i have my HD partitioned into 3 drives .. all presently being used by windows.
2. How do i uninstall Ubuntu first from virtualbox and convert that hard drive space in ntfs.

P.s. I really would not mind reinstalling windows all over again if that what it takes, but just need guidance.

---

### Post by 73ckn797 on 2009-03-05
Starting here: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) would do you a lot of good.

---

### Post by lenelson on 2009-03-05
If you have Windows XP on the computer, just install ubuntu and the partitioner in Ubuntu will set you up with Dual-boot.

---

### Post by aadil23 on 2009-03-05
But how do i first uninstall the Ubuntu i set up with virtualbox.

---

### Post by jlochhead on 2009-03-05
You should be able to delete the VirtualBox virtual machine simply by finding out where VirtualBox put the virtual machine and deleting the files manually...

You can install Ubuntu without having to re-install Windows. Doing so will be a little harder though.

A disk drive can hold up to 4 primary partitions or 3 primary and one extended partition. Inside the extended partition can be up to 16 logical partitions.

If you wanted to keep your current setup you would have to shrink your primary partitions (using GParted or Partition Magic) and create an extended partition in the free space.

You then need to create the necessary logical partitions inside the extended partition. You need a / (root partition), the closest equivalent is C:/ in Windows. I also recommend a swap partition, 2x the size of your RAM, this is the Linux equivalent of virtual memory.  

In addition, you can also create a /home partition. This is the Linux equivalent of user/youruseraccount. Basically this is where all the data for each user goes, this can be the files created by the user, user specific application data and general settings.

The advantage of the home partition is that if you re-install you can leave all your files and settings and they will still be there when you re-install. 

If you use a home partition the root partition should be somewhere in the region of 10-20 GB (my opinion). The home partition should be everything else minus the space required by swap.

If you don't use a home partition the root partition should be all the space minus that required for the swap partition.

---

### Post by Darkoan on 2009-03-05
Hi, Im a newbie too. I also have dual boot Ubuntu 8.10/ XPsp3.

1. Will i need to to a fresh/complete installation of Windows Once again before i install Ubuntu as i have my HD partitioned into 3 drives .. all presently being used by windows.
[COLOR="Red"]No need to reinstall - per above, you will just need to shrink your partitions to allow space for a new partition for Ubuntu.
While part of the Ubuntu installation allows you to set up your partitions, how you setup the partitions can be a bit confusing for newbie (like me). I recommend knowing a little bit about partitions, file systems (fat32 v nfts v ext3) and 'logical and primary and extended' partition. No need to be an expert, adn jlochead above explained most of it above.
In short
- shrink the windows partitions to allow space for Ubuntu
- create a primary ext3 '/' (called 'root')partition - 5-20GB
- create logical ext3 '/home' partition - most of the rest of the disk space
- creat /swap of 2gb - (in Ubuntu, at least with my installation, /swap was its own file system, ie no need to specify it to be ext3
-all new partitions are at 'beginning'
[/COLOR]

2. How do i uninstall Ubuntu first from virtualbox and convert that hard drive space in ntfs.
[COLOR="Red"]Im not an expert on virtualbox - I cant see a problem with a manual deletion.

Good luck[/COLOR]

---

