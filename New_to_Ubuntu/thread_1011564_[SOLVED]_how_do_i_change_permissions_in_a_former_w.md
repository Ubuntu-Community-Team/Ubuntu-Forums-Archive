---
title: "[SOLVED] how do i change permissions in a former windows drive?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by hoverX on 2008-12-14
I have a machine that used to run XP.  it has 3 partitions besides the one the OS is installed on.  I recently formatted it and installed Ubuntu 8.10 on the main partition.  When i try to change permissions of files on these extra partitions i get the message "you are not the owner so you cannot change permissions on this folder".  Do i have to do this command line "sudo something or other" or am i screwed?  alternatively, how do i run nautilus as superuser?

---

### Post by nhasian on 2008-12-14
to run nautilus as superuser you use:

```
gksu nautilus
```

you can change the ownership of a folder with *chown*.

---

### Post by drs305 on 2008-12-14
Assuming the filesystem is ext2/33, as your ubuntu one undoubtedly is, you can change the ownership as nhasian suggests. If any of the partitions remain as ntfs or fat16/32, the ownership is established during mounting and cannot be changed while the device is mounted, even with the sudo command.

Non-linux partitons can be mounted with specific ownership specifications from within the fstab file or with read/write permissions if mounted via the command line.

---

