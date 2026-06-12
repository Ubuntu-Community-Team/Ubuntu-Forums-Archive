---
title: "Fixed GRUB, but now can't boot into XP"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Go_Big_Blue on 2010-01-13
Yesterday, I was booting directly into Windows XP after installing Ubuntu 9.04.  Followed the instructions on this thread

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and it fixed the GRUB issue.  Unfortunately, now when I select the Windows XP OS to boot into it, it fails.  So I booted back into Ubuntu and looked at the partition editor, and received the following error on /dev/sdc1 (see attached image too)

```
Error(22): Opening '/dev/sdc1' as NTFS failed: Invalid Arguement
```

Anybody have any idea what may have happened here?

---

### Post by Go_Big_Blue on 2010-01-13
Bumpity, bump, bump.

---

### Post by Go_Big_Blue on 2010-01-13
Well, Winders XP is totally screwed.  I think (because this hdd is older and an IDE drive, not SATA) that the hdd in general is bad.  Going to use ddrescue off of the Ubuntu 9.10 Rescue Remix cd to copy the entire drive over to a new SATA hdd.  Then have to re-install Winders and fix GRUB all over again.  Yea!!

---

