---
title: "How do I fsck an external USB drive?"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by learningcurb on 2009-06-27
My external ext3 USB drive was mounted while my system crashed while I was messing around with a LiveCD.  (Copying large files into your live user's home folder while booted from a LiveCD is a bad idea by the way. :)).

Anyway, how can I run a filesystem check on the disk?  I tried "sudo tune2fs -c 1 /dev/sdc1" on the USB drive and mounted and unmounted it with no success.  Also, am I supposed to use e2fsck or fsck and do I need to boot into single user mode?  The dire warnings of possible file system corruption make me rather nervous.

I did read [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck) but it seems rather incomplete and it doesn't mention external drives.

Edit: I did some digging around, and it looks like maybe I want to use fsck.ext3.  However, should I use "fsck.ext3 /dev/sdb1" or "fsck.ext3 /dev/sdb"?  Also does the warning about being in single user mode only apply to doing a fsck on your root filesystem?

---

### Post by oldos2er on 2009-06-27
Never run fsck on a mounted partition.

   Can you post the output of this command (run with your USB drive on):
```
sudo fdisk -l
```

---

### Post by mcduck on 2009-06-28
> **learningcurb said:**
> My external ext3 USB drive was mounted while my system crashed while I was messing around with a LiveCD.  (Copying large files into your live user's home folder while booted from a LiveCD is a bad idea by the way. :)).

Anyway, how can I run a filesystem check on the disk?  I tried "sudo tune2fs -c 1 /dev/sdc1" on the USB drive and mounted and unmounted it with no success.  Also, am I supposed to use e2fsck or fsck and do I need to boot into single user mode?  The dire warnings of possible file system corruption make me rather nervous.

I did read [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck) but it seems rather incomplete and it doesn't mention external drives.

Edit: I did some digging around, and it looks like maybe I want to use fsck.ext3.  However, should I use "fsck.ext3 /dev/sdb1" or "fsck.ext3 /dev/sdb"?  Also does the warning about being in single user mode only apply to doing a fsck on your root filesystem?

For the command, use fsck. That works for every file system, as it detects what type the file system is and then calls the appropriate tool to do the actual checking.

And for the main question, unmount the drive, and then, assuming it's still /dev/sdb1 simply run following command:
```
sudo fsck /dev/sdb1
```

(and yes, the checking is doen for a partition, not for a drive, so you always check something like /dev/sda1, never /dev/sda)

---

### Post by anthony_barker on 2009-07-23
try gparted - it runs dosfsck -a -w -v

---

