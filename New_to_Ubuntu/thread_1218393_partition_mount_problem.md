---
title: "partition mount problem"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by raysa on 2009-07-20
I have three operating systems on my computer - Windows xp, Ubuntu 8.10 and Xubuntu 9.04 (This is by accident - when I installed Xubuntu 9.04 I meant to replace the old Ubuntu 8.10 but didn't).  

The xp partition with all its files is visible, mountable and fully accessible from Ubuntu 8.10.  But not from Xubuntu 9.04 - it doesn't show up in Places and if I try to sudo mount it I get "NTFS signature missing. /dev/sda1 doesn't seem to have a valid NTFS."  The sda1 partition is fat32 not ntfs.

How can I get my XP data files accessible from Xubuntu?

Thanks, Ray

---

### Post by Zenze on 2009-07-20
Did you try to mount it using the type option?

Try:
```
sudo mount -t fat /dev/sda1 /mountpoint
```

/mountpoint of course being the directory where you want to mount the filesystem.

---

### Post by raysa on 2009-07-21
Thanks, but when I tried this I got a message "unknown file system type 'fat' "  
Odd, because the system recognises two other drives which are fat-formatted.

---

### Post by mikechant on 2009-07-21
I believe it should be "vfat" not "fat".

---

