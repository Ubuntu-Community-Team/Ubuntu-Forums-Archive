---
title: "Automount partition on login (with permissions)"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by walawa on 2009-01-23
Hello, 
I currently have 3 partitions on my computer: 1 for ubuntu, 1 for windows and 1 shared where I keep my music library. I would like my shared partition to be mounted when I login (for use with media players). This partition is FAT32 is located in /dev/sda1. I've already tried creating a mountpoint (/media/sharedrive) and adding this line to /etc/fstab:  ```
#sharedrive
/dev/sda1 /media/sharedrive vfat defaults 0 0 
```
This worked fine at first but I noticed that after I rebooted, the partition would mount but I could not write to or add files. This problem disappears when I remove the line in fstab but then the drive won't automount. The problem seems to be in the fstab line so what could I add to fix this?

Thanks

---

### Post by drs305 on 2009-01-23
> **walawa said:**
> This worked fine at first but I noticed that after I rebooted, the partition would mount but I could not write to or add files. This problem disappears when I remove the line in fstab but then the drive won't automount. The problem seems to be in the fstab line so what could I add to fix this?

Good analysis. ntfs/vfat partitions make the owner of the mount point whoever mounted the device. So in this case it is mounted by root during the boot. You can specify a user in the fstab line. 

Assuming you are user 1000 (check with the "id" command if you aren't sure):
```

/dev/sda1 /media/sharedrive vfat defaults,uid=1000 0 0

```

For a bit more:
```

/dev/sda1 /media/sharedrive vfat auto,users,uid=1000,umask=027,utf8 0 0

```
which adds the ability for all users to mount/unmount the device, gives user 1000 ownership, and limits permissions for the group and others.

---

### Post by sam1948 on 2009-01-23
try this line of course with your directories
```
/dev/disk/by-label/XP   /media/XP  vfat   rw,user,suid,sgid,exec,auto  0   1
```

---

### Post by walawa on 2009-01-23
Thanks for your help! "/dev/sda1 /media/sharedrive vfat auto,users,uid=1000,umask=027,utf8 0 0" worked fine. sda1 now mounts with proper permissions.

---

