---
title: "Using unallocated space"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by japhyr on 2010-12-07
Hello,

I have been reading a number of threads about partitioning, but cannot seem to sort this out.  I created a multiple boot system with the goal of allowing two ubuntu installations and a windows installation.  I did this by installing windows first, then installing ubuntu.  When I installed ubuntu, I created root and home partitions for the current version, and a root and home partition that will be empty for now.  These will allow me to try new releases in a separate partition, thus leapfrogging versions.

The current partitions are:
- 100 MB windows system
- 40 GB windows OS
- 15 GB Ubuntu 10.04 root
- 51 GB ext4 with:
 - 15 GB ubuntu 10.04 home
 - 15 GB empty ext4
 - 15 GB empty ext4
 - 6 GB linux swap
- 212 GB unallocated

I have attached a screenshot of this setup from gparted.

I want to use the 212GB unallocated space for data.  I would like to format this ntfs, for compatibility with the windows system.  I booted a liveCD and used gparted, but I can't seem to do anything with the unallocated space because it is not part of any existing partition, and I have used all of the available primary partitions.

Do I have to reinstall ubuntu with the unallocated space part of the 51GB partition, or can I adjust this somehow?  I have no sensitive data on it yet, so reinstalling is not a big deal.  I have plenty of time to move partitions as well, so letting it run these operations for a couple hours is not a problem.

Any suggestions for how best to approach this?

---

### Post by amjjawad on 2010-12-07
> **japhyr said:**
> I booted a liveCD and used gparted, but I can't seem to do anything with the unallocated space because it is not part of any existing partition, and I have used all of the available primary partitions.


From the screenshot you attached, it shows that you already have Extended Partition which means you can create many logical partitions without any problem.

> Any suggestions for how best to approach this?

If I were you, I would make it much more simpler.
I have 9 OS's installed on my PC. 8 are Linux and 1 is Windows. Forget about Windows because it's on sdb. Let's talk about Linux.
First of all, you don't need /boot partition at all. That was old time when users had to do that but not anymore.
If you're planning for Triple Boot System then allow me to suggest the partition scheme for you (ONLY FOR LINUX):

[COLOR=Blue]sda5: Type ext4 - Mount Point (/) - You'll use this as the root partition for Linux Distro 1
sda6: Type ext4 - Mount Point (/home) - You'll use this as the home partition for Linux Distro 1[/COLOR]

[COLOR=Red]sda7: Type ext4 - Mount Point (/) - You'll use this as the root partition for Linux Distro 2
[/COLOR][COLOR=Red]sda8: Type ext4 - Mount Point (/home) - You'll use this as the home partition for Linux Distro 2

[COLOR=Black]sda9: Type is SWAP - you'll use this as shared SWAP partition for both Distro 1 and 2.

This is how I did with my system. Actually, I have only one home partition for my main OS but as long as you want to install only 2 Linux Distro Max at the moment, you could do the above scheme.

For more info, check this:
[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)
[/COLOR]
[/COLOR]

---

### Post by Megaptera on 2010-12-07
For the data-sharing aspect of your mission, this guide may be of help:
How To Harmonize Your Dual-Boot Setup for Windows and Ubuntu.

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by coffeecat on 2010-12-07
> **japhyr said:**
> I want to use the 212GB unallocated space for data.  I would like to format this ntfs, for compatibility with the windows system.  I booted a liveCD and used gparted, but I can't seem to do anything with the unallocated space because it is not part of any existing partition, and I have used all of the available primary partitions.

You need to enlarge your extended partition, sda4, first to take up all that unallocated space. Then you can create as many logical partitions in it as you wish, or just one big NTFS one. Windows will automatically pick up a new logical NTFS partition as E: or whatever drive letter it next allocates.

When you boot up with the live CD, it will probably automount your swap partition, sda8. Right-click on this in Gparted and choose 'swapoff'. Only then will you be able to enlarge the extended sda4 partition.

---

### Post by amjjawad on 2010-12-08
> > **coffeecat said:**
> You need to enlarge your extended partition, sda4, first to take up all that unallocated space. Then you can create as many logical partitions in it as you wish, or just one big NTFS one.

Yes, I'm sorry, I didn't read/notice carefully. 

Coffeecat is right.

If you still want to keep some unallocated space, then you could do that but after you enlarge your sda4 (extended) partition. I have 65GB and 100GB Partitions but they're unformatted and unused. I keep them just in case I need more space in the future.

---

