---
title: "How do I schedule a disk check on next boot?"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-06-23
How do I schedule fsck to run on next boot? I've heard of tune2fs, but does it work on an ext4 filesystem?

and how do I use tune2fs. I attempted to change the max-mount-counts to 1, but it didn't work. 

```
girdy@girdy-laptop:~$ tune2fs -c -1
tune2fs 1.41.4 (27-Jan-2009)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
    [-i interval[d|m|w]] [-j] [-J journal_options] [-l]
    [-m reserved_blocks_percent] [-o [^]mount_options[,...]] 
    [-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
    [-M last_mounted_dir] [-O [^]feature[,...]]
    [-E extended-option[,...]] [-T last_check_time] [-U UUID]
    [ -I new_inode_size ] device

```

any ideas?

---

### Post by LewRockwell on 2009-06-23
tag: scheduling

link: [http://www.addictivetips.com/ubuntu-linux-tips/install-and-use-task-scheduler-to-automate-tasks-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/install-and-use-task-scheduler-to-automate-tasks-in-ubuntu-linux/)

---

### Post by asuastrophysics on 2009-06-23
Thanks! :popcorn:

---

### Post by asuastrophysics on 2009-06-24
[Solved]Re: mark post as solved

---

### Post by learningcurb on 2009-06-27
I think you want to try:

> $ tune2fs -c 1 /dev/name_of_device


Where name_of_device is the partition you want to check. It's probably /dev/sda1 if you're using a SATA drive and /dev/hda1 for a IDE drive.  This is assuming your drive setup only has one drive and one partition though.  You can use "sudo fdisk -l" to list all your partitions and disks.

[http://embraceubuntu.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://embraceubuntu.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)

---

### Post by binbash on 2009-06-28
sudo touch /forcefsck

---

### Post by laurielegit on 2009-06-28
If you are gonna just do a straight reboot, this will work
```
sudo shutdown -rF NOW
```

But I don't recommend that for ubuntu: X will probabaly throw a hissy fit.

---

