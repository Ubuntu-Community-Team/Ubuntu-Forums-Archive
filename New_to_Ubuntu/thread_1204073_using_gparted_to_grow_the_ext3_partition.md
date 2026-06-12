---
title: "using gparted to grow the ext3 partition"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by Ajat on 2009-07-04
Hi.

Can someone give a step-by-step instruction to grow the ext3 partition?

here is obtained by using "parted" and "print"

```
(parted) print
Model: ATA FUJITSU MHY2120B (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  31.5GB  31.5GB  primary   ntfs         boot
 2      31.5GB  120GB   88.6GB  extended               lba
 5      31.5GB  98.6GB  67.2GB  logical   ntfs
 8      98.6GB  111GB   12.0GB  logical   ext3
 6      111GB   118GB   7518MB  logical   ext3
 7      118GB   120GB   1875MB  logical   linux-swap


```

Here is what i did:

At the beginning I have partition sda1 and sda5 in which i have windows installed.

First I just wanted to try kubuntu, and using gparted live, i shrinked 9 GB of partition sda5 to get 7 GB sda6 for root and 2 GB sda7 for swap.

I began to like this kubuntu and decided to give it more space. Then i started gparted again and shrinked more of sda5 to get 12 GB sda8.

Then using Gparted I copied the root partition (sda5) to sda8. Now i'm using my ubuntu through sda8 as /root. BUT sda5 is still there, and i want to add it to sda8, to have single 19 GB root partition. 

How is that possible? 

thanks

---

### Post by 73ckn797 on 2009-07-04
You will need to delete the partition that you want to use for the additional space. Then select the partition to grow and right click over it and select resize. Then using the mouse at the end next to the deleted space simply stretch the partition to take up the unused space. The partitions will have to be side by side in order to accomplish this.

---

### Post by ajgreeny on 2009-07-04
It should be possible but only with the live ubuntu or gparted CD, you will not be able to use your installed ubuntu to do it.

Run the live CD and open up partition editor.  If sda5 and sda8 are side by side it will be easier, but if they are in numerical order you will need to do the job in more than one stage.

What is sda6?  It is obviously a linux partition, but is it just data or something else, or is it empty?  In some ways it might make more sense with your space limitation to use just one partition for ubuntu, plus the small swap you already have.  Whichever you choose, you will need to delete sda5 so you can move/enlarge your current ubuntu root partition.

If you could add a screenshot of gparted it would make suggestions much easier as it will show how the partitions reside on the disk at the moment.

---

### Post by drs305 on 2009-07-04
You probably have already found this out, but remember these things:

Backup important data before doing any of this.

It will have to be done from a LiveCD, gparted CD, systemrescueCD, etc since your ubuntu system can't be mounted.

Moving the partitions will take a long time since all the data in 8 is going to be moved to a different location.

Note the uuid's and device designations after you have done all this to make sure your system will still boot. The UUIDs/sdX designations may change during all this. Check by running these commands and edit if necessary:
```

sudo blkid -c /dev/null  # check new UUIDs
cat /boot/grub/menu.lst  # Check the UUIDs in the bottom area that lists the boot options
cat /etc/fstab  # check to make sure UUIDs are correct, sdXX are correct if any are listed
cat /etc/initramfs-tools/conf.d/resume  # check UUID of swap partition

```

Added: If any of the menu.lst or fstab information is incorrect, you can change it from the LiveCD and will want to do this before rebooting. To edit these files you will have to make a mount point and then mount the new system partition to that mount point. For example, make a mount point of /mnt/temp, then mount your new system partition (for example sda5 or whatever it is, to /mnt/temp). Then you would edit your real system files (not the LiveCD's files) by editing /mnt/temp/etc/fstab...

---

### Post by Ajat on 2009-07-05
Thanks all :)

---

### Post by LewRockwell on 2009-07-05
> **Ajat said:**
> Thanks all :)

you might enjoy these:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[http://www.partedmagic.com/](http://www.partedmagic.com/)


also, please edit the title in your first post to include "[SOLVED]" at the beginning

thanks

.

---

