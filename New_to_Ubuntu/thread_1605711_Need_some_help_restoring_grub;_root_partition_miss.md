---
title: "Need some help restoring grub; root partition missing from Places menu"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by diablo75 on 2010-10-25
Yesterday I had a dual-boot system lose Windows due to the NTFS file system more or less breaking from reaching critical mass (in terms of the number of files it THOUGHT were on the hard drive versus what was literally there).  So I used some data recovery software to get my important files off of it and then just finished reinstalling it here.  During install I selected the previous Windows partition, deleted it, and created  a new one (quick format).  No issues during install.  Now I'm trying to set grub back up.

I'm following the guide that's shown here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Right off the bat it asks you to mount your "Ubuntu partition" (doesn't say anything more specific than that, but I'm sure it means your / or /boot partition if you had one) by clicking on it in the Places menu while running from a Live CD.  Unfortunately this partition doesn't appear in Places; only my /home partition, the Windows partition and an external hard drive I have plugged in are showing up.

I've attached a screenshot of what the hard drive partitions look like from within Windows Storage management utility.  And below is the output of sudo fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9697acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13944   112005148+   7  HPFS/NTFS
/dev/sda2           13945      121601   864754822    5  Extended
/dev/sda3           22455      120951   791177152+  83  Linux
/dev/sda5           13945       22454    68356543+  83  Linux
/dev/sda6          120952      121601     5221093+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x542be781

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

I'm pretty sure my root partition is sda5, but I don't know why it wouldn't be appearing in Places.  Could it have errors?  Am I able to run fsck against it from the Live CD?  What should I do next?

---

### Post by diablo75 on 2010-10-26
Bump.

I think all I need to do is manually mount sda5... but I'm not very sure about how to do that correctly.  Any help?

---

### Post by drs305 on 2010-10-26
You mentioned both / and /boot? Do you have a separate /boot partition? If not, from the LiveCD:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note in the second command you do NOT put the partition number.

You do have 2 Linux partitions. If you aren't sure if sda5 is the correct partition, after you run the first command, inspect the contents for the normal Ubuntu folders, ***including*** /boot:
```
nautilus /mnt
```

If you know you have a separate boot partition, mount it as well before running the install command:
```
sudo mount /dev/sda3 /mnt/boot
```

---

### Post by Quackers on 2010-10-26
If sda5 is your root partition

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Edit: Aha, the Grub Master beat me :-)

---

### Post by diablo75 on 2010-10-26
> **drs305 said:**
> 

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```



These exact two commands did the trick!  You're awesome!  Thanks!
:guitar:

---

