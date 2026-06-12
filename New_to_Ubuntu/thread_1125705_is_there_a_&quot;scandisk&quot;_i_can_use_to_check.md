---
title: "is there a &quot;scandisk&quot; i can use to check my ipod with?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-14
hey all,

is there some sort of program i can use to scan and attempt to fix bad sectors on an ipod?
microsoft has scandisk, i think ubuntu has fdisk.

does fdisk scan usb drives?

---

### Post by halitech on 2009-04-14
[http://en.wikipedia.org/wiki/Fdisk](http://en.wikipedia.org/wiki/Fdisk)

fdisk (for "fixed disk") is a commonly used name for a command-line utility that provides disk partitioning functions in an operating system. However, each version of fdisk is independent of the others, and aside from their name and similar purpose, they are unrelated.

you're thinking of fsck

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

The system utility fsck (for "file system check" or "file system consistency check") is a tool for checking the consistency of a file system in Unix and Unix-like operating systems such as Linux.

---

### Post by asuastrophysics on 2009-04-14
fsck seems to assume that i only want to check ext3 and ext2 file systems:

```
girdy@girdy-desktop:/dev$ sudo e2fsck -b 8193 /dev/sdb3
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: No such file or directory while trying to open /dev/sdb3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

girdy@girdy-desktop:/dev$ fsck /dev/sdb1

```

how do i make it check the ipod?
i don't even know if /dev/sdb1 is the correct address
if i right-click on my ipod, it shows nothing about which directory in /dev it comes from. 
so how do i verify the ipod's directory in /dev
and where in the line "sudo fsck /dev/sdb1" do i insert "fat32"?

---

### Post by halitech on 2009-04-14
```
sudo fdisk -l
``` will give you the layout of the drives connected to your system. I'm not sure what file system the ipod uses so you may want to borrow a windows or mac system to check the ipod on if you are concerned about possible issues with it.

---

### Post by asuastrophysics on 2009-04-14
thanks man!

---

