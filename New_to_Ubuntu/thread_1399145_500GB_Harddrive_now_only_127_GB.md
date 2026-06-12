---
title: "500GB Harddrive now only 127 GB"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by htebcam on 2010-02-05
I originally installed Ubuntu onto a new 500 GB harddrive, but then I needed to install windows XP. So I removed Ubuntu by entering the terminal, then the root directory and typed gparted which brought up a new window. I selected the “/” directory in the partition table for deletion, and this also removed the swap partition.

  I then installed XP, but now instead of having 500 GB my harddrive shows only 127 GB.  Is there a reason for this, and a solution (not too techie) to get back the missing  memory?

I intend installing Ubuntu again, using a dual boot, but firstly I'm concerned about the lost capacity.

---

### Post by falconindy on 2010-02-05
Sounds like you're using the original (unpatched) XP install disc. It wasn't until SP1 that the OS supported 48-bit LBA. If you load a service pack on top of the install, you'll be able to reclaim the missing space as a second drive. If you have an install CD with a service pack already included, then you can use that to format and install to the entire 500gb.

---

### Post by htebcam on 2010-02-05
> **falconindy said:**
> Sounds like you're using the original (unpatched) XP install disc. It wasn't until SP1 that the OS supported 48-bit LBA. If you load a service pack on top of the install, you'll be able to reclaim the missing space as a second drive. If you have an install CD with a service pack already included, then you can use that to format and install to the entire 500gb.
It's service pack 2, and I've installed XP and the service pack before on another hardrive without this  problem. I'm wondering if i've damaged something whilst deleting Ubuntu, if that's possible?

---

### Post by Jackzor on 2010-02-05
When you installed windows did you delete all the partitions on the drive? If you left the ubuntu partition then windows can't see it. Boot to the windows xp cd and look at the partition table. you should be able to see all the partitions on the drive tell us what you see

---

### Post by halitech on 2010-02-05
try booting from an Ubuntu Live cd and open a terminal and run
```
sudo fdisk -l
```
thats a lower case L, not the number 1

---

### Post by htebcam on 2010-02-05
> **halitech said:**
> try booting from an Ubuntu Live cd and open a terminal and run
```
sudo fdisk -l
```
thats a lower case L, not the number 1
I ran the command, and this is the read-out:

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 

ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x0007931e 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS 

Disk /dev/sdb: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xa4b57300 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS 
ubuntu@ubuntu:~$ ^C 
ubuntu@ubuntu:~$

---

### Post by audiomick on 2010-02-05
You seem to have 2 500GB drives in the machine.
The first one, /dev/sda , has a single NTFS partition on it of   134206978kB.
I expect that this is the partition that your XP is in, and that the rest of the drive is unallocated.

The second, /dev/sdb , has a single NTFS partition of 500GB on it.

I would boot into the Ubuntu live CD and expand the partition on the first drive to take up the whole drive, or, if you are planning on installing Ubuntu to that drive anyway, just run the installer and use the "manual" partitioning option to set up your Ubuntu partitions in the empty space.

---

