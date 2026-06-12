---
title: "[SOLVED] Gparted alternaitves"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-15
Server is 8.10 with two storage drives attached. One of the storage drives has an NTFS partition on it, and I would like to remove this NTFS partition. Fdisk has failed to succesfully remove the partition. And Gparted will not run on the server because of a VGA incompatibility. So are there any other recommended programs that I can try? Preferable something can be run from SSH Thanks.

---

### Post by pshootr on 2008-12-15
I think I may try booting from a live cd, may be I can do it like that.

---

### Post by Tatty on 2008-12-15
Yes booting from a live CD will work.

Why did fdisk fail?

---

### Post by pshootr on 2008-12-15
> **Tatty said:**
> Yes booting from a live CD will work.

Why did fdisk fail?

Here is the message I got.

pshootr@LinuxFS:~$ WARNING: Re-reading the partition table failed with error 22: Invalid argument.

---

### Post by oldos2er on 2008-12-15
parted is the CLI version of gparted. There's also cfdisk.

---

### Post by starcannon on 2008-12-15
Googling your error came back with a resounding "use Ranish"

So I guess try out the Ranish Partition Manager, sounds like its worked wonderfully for fdisk and cfdisk error 22:
[http://www.ranish.com/part/](http://www.ranish.com/part/)

GL and have fun, keep us posted on how it turns out (write us an error 22 work around guide?)

---

### Post by pshootr on 2008-12-15
fdisk -1
Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4982    40017883+  83  Linux

tr@Linux:~$ sudo parted
GNU Parted 1.8.9
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.

(parted) select sdc1
Error: Could not stat device sdc1 - No such file or directory.  
Retry/Cancel?

Have not tried ranish yet. Figured I would try parted first. Above fdisk shows sdc1 as a linux system format. But when I select sdc1 in (parted) it says no such file or directory. (because it is not mounted yet?)

Before I did this I booted from live cd and deleted old partition and created a new one. But for some reason the new partition had 700 megs worth of linux folders on it. Created by live cd I guess. So then I thought I would recreate the filesystem using parted.

---

### Post by pshootr on 2008-12-15
long story short. I used 

sudo mkfs -t ext3 /dev/sdc1  And then mounted. All seems fine. Thanks for the help guys. Yall :guitar:

---

