---
title: "system will not start asking for manual fsck"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by haiyun211 on 2009-08-14
Hi guys my system will no longer start it says it failed fsck on root and says there Haas to be a manual one done and I don't even know where to begin

---

### Post by haiyun211 on 2009-08-15
Found some info on the forum and it will not authenticate the the su -  command and when i try to run fsck it says i do not have permission to do so.  When I run it without my laptop plugged in it skips the system file scan and will let me login but when plugged in thats when i have these problems I do not know enough about ubuntu to really try to diagnose it on my own.  Any help would be very appritiated.:(

---

### Post by bodhi.zazen on 2009-08-15
Boot the desktop (live cd)

open a terminal

enter ```
fsck -y /dev/sda1
```

change /dev/sda1 to the partition that needs to be repaired.

---

### Post by haiyun211 on 2009-08-15
Ok I don't know if i screwed up but after it was done and i rebooted the grub menu says error 17

---

### Post by bodhi.zazen on 2009-08-15
It sounds as if either your file system is corrupt beyond repair or your hardware is failing.

If you need to recover data, you can try testdisk and photorec.

Otherwise you can try to re-install but be warned the HD may be about to fail.

---

### Post by haiyun211 on 2009-08-15
How do I go about doing this testdisk if I cant get past grub?

---

### Post by haiyun211 on 2009-08-17
Thanks for all your help.  I just decided to reinstall since I already had most of my important stuff backed up on my Ipod.  Thanks again.

---

