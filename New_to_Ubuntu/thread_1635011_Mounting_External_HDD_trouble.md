---
title: "Mounting External HDD trouble"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-12-01
I'm currently running Ubuntu 10.10 and trying to write something to a friends external HDD. The problem is, he has it set to back-up on a macbook and every time I try to write to it, it says its on read-only mode and I have no idea how to mount it. I've never had this problem with my HP external HDD that I run through Wine. My friends external HDD is a acomdata passport if that helps

---

### Post by desnaike on 2010-12-01
How is it formatted mac hfs windows ntfs or fat32/16

ubuntu will write fat not sure of ntfs will not write hfs

---

### Post by Captainflowers91 on 2010-12-01
Its mac formatted. Windows won't even recognize it when I tried it on there.

---

### Post by CharlesA on 2010-12-01
If it's formatted as a Mac File system, it should obey permissions, but if the users are different from the mac and your machine, it'll be a bit of a pain to write files to it.

Post the output of this:

```
mount
```

---

### Post by Captainflowers91 on 2010-12-01
/dev/sda3 on / type xfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/captainflowers/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=captainflowers)
/dev/sdb2 on /media/Time Machine Backups type hfsplus (rw,nosuid,nodev,uhelper=udisks)

---

### Post by CharlesA on 2010-12-01
Ah, it's set for hfsplus.

It looks like it's a pain to get that to give you read/write access in Ubuntu.

See [here]("https://help.ubuntu.com/community/hfsplus").

---

### Post by Captainflowers91 on 2010-12-01
Alright, thanks for the help

---

