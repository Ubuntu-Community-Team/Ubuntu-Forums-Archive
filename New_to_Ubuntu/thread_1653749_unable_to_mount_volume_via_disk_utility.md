---
title: "unable to mount volume via disk utility"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by danielstephens81 on 2010-12-27
Hi there,

I'm not familiar enough with ubuntu and need some help... presently use a dual boot system with ubuntu 10.04 LTS and windows on the same hard disk. The hard disk is 320 GB and when installing ubuntu I created a 'data' partition (172 GB) to keep all my linux data files. Files on the 'data' partition are accessed using 'mount volume' from the Disk Utility.

But this doesn't seem to work anymore?? The 'mount volume' option has vanished and all I see is 'create partition'. Two separate things I did recently that could have caused it (i) logged into windows at startup and (ii) ran the update manager in ubuntu. Would anyone be able to advise how I should proceed? Have I lost my data?

Many thanks for your time.

Daniel

---

### Post by seawolf167 on 2010-12-27
Can you run 

```
sudo fdisk -l
```

in a terminal and post the output here

---

### Post by danielstephens81 on 2010-12-28
Many thanks for your reply,


The output from the fdisk command is as follows:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x224f224f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1722    13824000   27  Unknown
/dev/sda2   *        1722        1734      102400    7  HPFS/NTFS
/dev/sda3            1734       10658    71680000+   7  HPFS/NTFS
/dev/sda4           10658       38914   226962433    5  Extended
/dev/sda5           10658       17032    51200000+  83  Linux
/dev/sda6           37883       38914     8279040   82  Linux swap / Solaris
daniel@daniel-laptop:~$ 


it looks like the partition I'm trying to mount doesn't appear here either... sda5, sda6 & the missing partition are part of sda4... if that makes sense. I probably haven't used the proper terminology. Many thanks for your reply.

Daniel

---

### Post by seawolf167 on 2010-12-28
This is your root linux-based system ( / )

```
/dev/sda5           10658       17032    51200000+  83  Linux
```This is your swap file (swap)

```
/dev/sda6           37883       38914     8279040   82  Linux swap / Solaris
```By booting into Ubuntu, we know that these two partitions are working ok

This is a pre-installed hidden "rescue" partition installed by the manufacturer.

```
/dev/sda1               1        1722    13824000   27  Unknown
```These two are your windows partitions

```
/dev/sda2   *        1722        1734      102400    7  HPFS/NTFS
/dev/sda3            1734       10658    71680000+   7  HPFS/NTFS
```From what I can see you don't have any "missing" partitions or unallocated space.

You can see what Ubuntu is mounting upon boot by viewing the file /etc/fstab (this will most likely only have 3 entries: proc, / and swap). Make sure you have a backup of this if you are going to try to edit anything!


From what I read in your original post, you are mounting a "data" partition that you original created and accessed through windows.

We can easily mount these windows partitons, we just create a "home" for it, then mount it (note that the * indicated a bootable partition, so sda3 most likely your "data" partition):

Create mount directories

```
sudo mkdir /mnt/ntfs-sda2
sudo mkdir /mnt/ntfs-sda3
```Mount the NTFS parttion in the directories we just created

```
sudo mount /dev/sda2 /mnt/ntfs-sda2
sudo mount /dev/sda3 /mnt/ntfs-sda3
```Then you can simply browse the in the Ubuntu file manager (open a window, then browse to /mnt/ntfs-sda2 or 3)

To unmount the partition you can give the mount point or the partition

```
sudo umount /mnt/ntfs-sda2
or
sudo umount /dev/sda2
```If this is what you are looking to do, the next step would be to add an entry into /etc/fstab so that the partition is mounted upon boot.

---

### Post by danielstephens81 on 2010-12-28
Hi there,

Many thanks for the clear explanation. The 'missing' volume I was referring to is the space between sda5 & 6.

Device Boot Start End Blocks Id System
/dev/sda1 1 1722 13824000 27 Unknown
/dev/sda2 * 1722 1734 102400 7 HPFS/NTFS
/dev/sda3 1734 10658 71680000+ 7 HPFS/NTFS
/dev/sda4 10658 38914 226962433 5 Extended
/dev/sda5 10658 17032 51200000+ 83 Linux
/dev/sda6 37883 38914 8279040 82 Linux swap / Solaris

As sda5 runs from 10658 to 17032 but sda6 runs from 37883 to 38914. The space between 17032 and 37883 is unaccounted for. It's that space that I would like to recover. I created this partition using the ubuntu live cd and not from windows a few months back and everything worked nicely since then. Do you think this is something that can be fixed....?

Once again, many thanks for your time.

Daniel

---

### Post by seawolf167 on 2010-12-28
Didn't even notice that; I'd try to recover the missing partition before anything else using:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


A quick search for other links/info:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://ubuntuforums.org/showthread.php?t=525866"]
http://ubuntuforums.org/showthread.php?t=525866[/URL]


See if any of those help you out/work.

---

### Post by danielstephens81 on 2010-12-30
Many thanks, I'm going to give that a try. Will send an update once I get it to work. Kind regards,

Daniel

---

