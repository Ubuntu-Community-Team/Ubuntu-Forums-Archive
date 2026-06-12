---
title: "fdsk"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by fleamour on 2009-09-05
How do I manually run fdsk under Xubuntu & see results?  Kinda like you can run chkdsk from within the Recovery Console.  I've been told you cannot run fdsk on a mounted file system?  Is there a GUI interface like SpeedFan app that give you a health run-down on your disks?

Also if I run chkdsk/fdsk from respective Windows/Linux partitions, how do they treat the respective NTFS/ext3 formatted partitions?

---

### Post by halitech on 2009-09-05
are you referring to fdisk or fsck? fdisk can be run no matter if the partition is mounted or not. fsck can only be run on unmounted partitions. not sure on a gui app for fsck but you can use Partition Editor to see your partitions.

---

### Post by Liolikas on 2009-09-05
```

man fdisk
man chkdsk

```

---

### Post by Bodsda on 2009-09-05
> **fleamour said:**
> How do I manually run fdsk under Xubuntu & see results?  Kinda like you can run chkdsk from within the Recovery Console.  I've been told you cannot run fdsk on a mounted file system?  Is there a GUI interface like SpeedFan app that give you a health run-down on your disks?

Also if I run chkdsk/fdsk from respective Windows/Linux partitions, how do they treat the respective NTFS/ext3 formatted partitions?

If you mean fsck, then yes the file system must be unmounted. You can boot to recovery console from grub and run from there if you wish. Generally, I have had no need to run it apart from when my hard drive blew up, and then the check was run automatically for me.

Hope this helps,
Kind regards,
Bodsda

> **Liolikas said:**
> ```

man fdisk
man chkdsk

```

define:helpful

---

### Post by fleamour on 2009-09-05
> **halitech said:**
> are you referring to fdisk or fsck?

What's the difference?

---

### Post by Bodsda on 2009-09-05
> **fleamour said:**
> What's the difference?
fdisk is a way of interfacing and manipulating your drive partitions, while fsck is a filesystem checker. Although you are probably better off using e2fsck as it was designed for ext2/3 filesystems in particular

---

