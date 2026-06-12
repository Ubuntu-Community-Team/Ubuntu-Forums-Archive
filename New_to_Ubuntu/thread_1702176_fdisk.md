---
title: "fdisk"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by beacon on 2011-03-07
When I type fdisk -l, nothing appears. Can someone tell me what I am doing wrong? Many thanks.

---

### Post by Rubi1200 on 2011-03-07
Did you preface the command with sudo?

What exactly are you trying to do?

---

### Post by beacon on 2011-03-07
Thank you Rubbi. Yes, I did use sudo.

I am trying to install a transcend portable hard drive. The instructions they give for Linux are not altogether clear, and the command to mount does not work. I though I could learn something from fdisk that would let me know what command to use.

---

### Post by oldfred on 2011-03-07
I still type a command and find it does not work, even fdisk still. I have to go back and add sudo.

More info on mounting. If your external partitioned? You mount partitions not drives.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by Rubi1200 on 2011-03-07
Could you give us a link to their instructions or post it here please?

With most external drives you should be able to just plug it in and Ubuntu will recognize it.

How is BIOS set regarding boot device priority?

---

### Post by beacon on 2011-03-08
Thanks to both of you for your help. The link is [http://uk.transcend-info.com/support/dlcenter/Manual/Manual-SJ25M-EN.pdf](http://uk.transcend-info.com/support/dlcenter/Manual/Manual-SJ25M-EN.pdf)

However, the relevant part for me is as follows:

Driver Installation for Linux
™
 Kernel 2.4, or Later 
No drivers are required. Plug your StoreJet 25 into a USB port and mount it. 
1.  First create a directory for the StoreJet 25. 
Example: mkdir /mnt/Storejet
2.  Then, mount the StoreJet 25. 
Example: mount –a –t msdos /dev/sda1 /mnt/Storejet 

I don't know about whether Storejet is a partition, but the instructions do say to 'mount' it. I have done step 1 but don't know what command will work for step2.

---

### Post by oldfred on 2011-03-08
I had not seen a mount with msdos. All the info has either vfat or ntfs. But it looks like the msdos is an older 8.3 dos support where vfat supports long file names. (man mount shows msdos as an option). The ntfs also lets you support larger files where FAT has a max of 4GB.

The example shows mounting sda1 so it must be partitioned but is probably sdb1. Some USB devices get mounted at higher letters also like sdf. Usually if you have a multiport USB device plugged in.

If you do this what is shown?

```
sudo fdisk -lu
```Then you will know where to mount it. I would also use vfat not msdos.

---

### Post by beacon on 2011-03-08
Thanks very much Oldfred. When I typed fdisk -lu I got the following:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dcec8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   973701119   486849536   83  Linux
/dev/sda2       973703166   976771071     1533953    5  Extended
/dev/sda5       973703168   976771071     1533952   82  Linux swap / Solaris

Disk /dev/sdf: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a581c

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdg: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd37c59ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63   625137344   312568641    c  W95 FAT32 (LBA)


Whether I type vfat or msdos I get the same message -- a lengthy note about what mounting involves, but it means little to me in my present state of knowledge. I have made several trial and error stabs, but haven't succeeded.

I am sorry to bother you again, but I wonder if anything I have added gives you enough information for another suggestion.

Thanks.

---

### Post by oldfred on 2011-03-08
Which is your StoreJet?

You show sdf at 123.5GB and no partitions. I think you will have to create a partition or two to use it.

You show sdg with 320GB and one partition sdg1.

You can mount sdg1 with

$ sudo mkdir /Data
$ sudo mount /dev/sdg1 /Data
where sdg1 needs to be your drive, partition

It will try to guess the format (FAT) and mount it. This default may not give you all the permissions for read & write that you want and with FAT or NTFS you have to include those with the mount command.
You also should see the sdg1 in your Places, left panel.

To partition sdf, you can use gparted. It must be unmounted. Your install does not include gparted where the liveCD does, since you can only work on unmounted drives/partitions. But you can download gparted from synaptic - System, Administration, synaptic search on  gparted.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[URL="http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/"]
[/URL]

---

### Post by beacon on 2011-03-08
Thanks for the quick and (I hope) helpful reply. I'm not going to be able to digest and try it immediately, but I'll let you know how I get on. It's good of you to help.

---

