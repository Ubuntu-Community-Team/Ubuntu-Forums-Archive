---
title: "Formatted partition with a mount point, now giving error"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Redmage913 on 2011-02-17
Greetings,

I'm working on a Gateway T-Series laptop with Ubuntu 10.04 on it. It has multiple partitions, the first being for Windows XP when I get it on here, the second for Ubuntu, the third for data accessed from both OSes.

When I first installed Ubuntu, I gave that third partition a mount point. I have since formatted it into FAT32 (gparted didn't let me give it a mount point).

Now, every time I start the machine up, I get the following error:

> The disk drive for /blah is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recoveryHow do I remove whatever entry is in the computer for /blah ?

Thanks,

--Red

---

### Post by mikewhatever on 2011-02-17
You have to remove the formatted partition from /etc/fstab.


run the following to open the file for editing:
```
gksudo gedit /etc/fstab
```

---

### Post by Foxheadz on 2011-02-17
You would have to manually specify it in fstab (/etc/fstab) post what that file looks like please.

---

### Post by Redmage913 on 2011-02-17
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=c6064219-9d16-4d6e-a96a-1ab49e9fe86c /               ext4    errors=remount-ro 0       1
# /blah was on /dev/sda4 during installation
UUID=1eaa9924-3406-4921-bccf-b2c85d0a29d0 /blah           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=51ddbcb2-012d-465a-962a-8592c9918ff3 none            swap    sw              0       0

```

---

### Post by Foxheadz on 2011-02-17
```
UUID=1eaa9924-3406-4921-bccf-b2c85d0a29d0 /blah           ext4    defaults        0       2
``` if the only thing you changed was making it fat32 then it's possible that just changing ext to fat32 might fix it. If not i'm guessing the uuid might of changed.

---

