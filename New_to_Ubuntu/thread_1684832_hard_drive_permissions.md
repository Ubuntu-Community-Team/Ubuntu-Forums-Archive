---
title: "hard drive permissions"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by bambie on 2011-02-09
I am having problems with my hard drive with all my data. I have 2 hard drives

1) Holds Windows 7 and Ubuntu 10.10 OS's
2) Holds All my data like music, videos ect

I have other users on my ubuntu but they can not see or access hard drive 2. 

I have tried terminal with chmod in terminal and i have tried right clicking it in /media/ and setting permissions that way. I have tried setting users to administrators and Still no luck :( 

I have also tired to do it on folders and files in the hard drive with no luck.

The command I have tried using is:

chmod o+rwx Data  and then ls -l to check but it has not changed a thing. 

The hard drive is the following setup in disk utility:

Usage: Filesystem
Partition Type: NPFS/NTFS (0x07)
Partition Flags: -
Type: NTFS

Any help so that my other users can see the hard drive would be great. Also is there a way for me to have it auto mount when i login.

---

### Post by robsoles on 2011-02-09
Welcome to UF!

If you just want everybody who uses the PC to be able to use it then set it up in /etc/fstab

guide: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by oldos2er on 2011-02-10
> **bambie said:**
> chmod o+rwx Data  and then ls -l to check but it has not changed a thing.

NTFS doesn't know anything about Linux permissions, you need to set them when the disk is mounted. [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

