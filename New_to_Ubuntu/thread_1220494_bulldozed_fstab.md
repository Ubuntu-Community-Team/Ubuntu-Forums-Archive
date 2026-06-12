---
title: "bulldozed fstab"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by sandyd on 2009-07-22
um...i just stupidly overwote my fstab file.

Now that im not daring to shut down my computer becasue i know nothing is agonna work, can someone give me a pointer to fix my stupid mistake?

---

### Post by unutbu on 2009-07-22
Does /etc/fstab~ or /etc/fstab.BAK exist?

If they do not exist, then please post the contents of /etc/mtab
and the output of 
```

sudo blkid -c /dev/null
```

---

### Post by masterkoppa on 2009-07-22
Try doing:

```
sudo dpkg --reconfigure util-linux
```

Also try reading man fstab

Good Luck with this issue

---

### Post by sandyd on 2009-07-22
no backups it seems...


```
/dev/sda1: UUID="E8C42C2DC42BFD06" TYPE="ntfs"
/dev/sda5: UUID="615809e4-9aa2-4a32-a31a-0bdc7b2ebf7f" TYPE="ext3"
/dev/sda6: UUID="09078d6b-c8f1-41ce-bae8-f56f8fe8c2de" TYPE="swap"

```

---

### Post by sandyd on 2009-07-22
```

/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda1 /media/win_xp fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/dolphinaura/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=dolphinaura 0 0

```

---

### Post by unutbu on 2009-07-22
Save this in /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=E8C42C2DC42BFD06 /media/win_xp ntfs rw,nosuid,nodev,allow_other,blksize=4096 0 2
# /dev/sda5
UUID=615809e4-9aa2-4a32-a31a-0bdc7b2ebf7f / ext3 rw,relatime,errors=remount-ro 0 1
# /dev/sda6
UUID=09078d6b-c8f1-41ce-bae8-f56f8fe8c2de none swap sw 0 0
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0

```
I'm afraid I don't know of a way to test if this will work without rebooting.

---

### Post by ecmatter on 2009-07-22
fsck uses /etc/fstab to check the root partition.  Might be worth it to run fsck and see what it spits out before rebooting.

---

### Post by sandyd on 2009-07-23
thanks! fstab file fixed problem

---

