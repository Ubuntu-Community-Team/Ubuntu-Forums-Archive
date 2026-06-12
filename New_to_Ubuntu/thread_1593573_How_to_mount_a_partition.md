---
title: "How to mount a partition"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by webwiller on 2010-10-11
Hi all!
For some reason I was not able to mount one partition during installation process and I would need to mount it now.
Could you please tell me the commands in order to mount my partition under /mnt/data having all permissions to read/write??

TX in advance!

WW

---

### Post by celticbhoy on 2010-10-11
What file system is it formated to? FAT, EXT, NTFS?

---

### Post by webwiller on 2010-10-11
> **celticbhoy said:**
> What file system is it formated to? FAT, EXT, NTFS?

NTFS, cause is a "data" partition shared by win7 and ubuntu.

---

### Post by celticbhoy on 2010-10-11
ntfs-config should do the trick

sudo apt-get install ntfs-config

---

### Post by oldfred on 2010-10-11
Sometimes NTFS-config does not do it correctly. It is worthwhile to understand how mounting & fstab work.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

My entry:
```
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

```

---

### Post by wkhasintha on 2010-10-11
Use this tool. It's GUI tool to easily configure fstab.

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

---

