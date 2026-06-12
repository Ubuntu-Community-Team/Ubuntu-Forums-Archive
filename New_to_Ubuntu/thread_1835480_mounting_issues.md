---
title: "mounting issues"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by coolmego on 2011-08-29
""[sd_coolmego@coolmego /]$ sudo mount /dev/sda2 /mnt/e_drive/
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.""


 how to  fix this problem?

---

### Post by seawolf167 on 2011-08-29
Can you please post the output of the following commands in CODE tags.

```
sudo fdisk -l
mount
sudo blkid
cat /etc/fstab
ls /mnt
```

---

### Post by mcduck on 2011-08-29
> **coolmego said:**
> ""[sd_coolmego@coolmego /]$ sudo mount /dev/sda2 /mnt/e_drive/
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.""


 how to  fix this problem?

Sounds like you are dual-booting or using that drive/partition on a windows machine. In that case the easiest way to fix the problem is to boot into windows, let it fix fix it's own mess, and then make sure you shut down correctly (or safely remove the drive if it's an external one). That should remove the unclean mark from the drive.

---

### Post by Mark Phelps on 2011-08-29
> **coolmego said:**
> ""[sd_coolmego /]$ sudo mount /dev/sda2 /mnt/e_drive/
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.""


 how to  fix this problem?

Since this has a drive "letter", I'm assuming that it is a Windows partition, right? Hopefully, it was NOT your Win7 OS partition, otherwise, to fix, you boot into Win7 and run CHKDSK on it.

---

### Post by coolmego on 2011-08-30
thank you for the reply the problem was solved after running the mount-command again.

---

