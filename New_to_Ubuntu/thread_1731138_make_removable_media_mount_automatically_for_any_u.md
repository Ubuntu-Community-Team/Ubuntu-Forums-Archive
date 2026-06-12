---
title: "make removable media mount automatically for any user"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by porphyry5 on 2011-04-16
10.10 with fluxbox
Trying to make removable media mount automatically for any user, I included these lines at the end of fstab
```
/dev/dvd  /media/dvd  udf,iso9660  user,auto,exec,utf8  0  0
# FAT ~ Linux calls FAT file systems vfat
# /dev/sda1
UUID=315F-7641  /media/128m  vfat auto,user,uid=1000,gid=100,dmask=000,fmask=111,utf8  0  0
# /dev/sdc1
UUID=34A8-64F5  /media/4gb  vfat auto,user,uid=1000,gid=100,dmask=000,fmask=111,utf8  0  0
# NTFS ~ Use ntfs-3g for write access (rw) 
# /dev/sdd1
UUID=1CDC2B8BDC2B5E70  /media/16gb  ntfs-3g  auto,user,uid=1000,gid=100,dmask=000,fmask=111,utf8  0  0
```and according to [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) that should do it.  But this is what happens
```
g@default:~$ ls -l /media/4gb
ls: cannot access /media/4gb: Permission denied
g@default:~$ su -
Password: 
root@default:~# ls -l /media/4gb
total 64
-rw-rw-rw- 1 1000 users 1559 2011-04-16 13:18 OrchidSchedule.txt
root@default:~# xedit &
```I've also tried setting dmask, fmask and umask together to both 000 and 777, makes no difference.

---

### Post by scott-ian on 2011-04-16
An easy way would be to go into System --> Administration --> Users and Groups, select the user, click "advanced setings" and under the "User Privileges" tab, check "Mount user-space filesystems."  You would have to do this individually for each user, but I think it would work.

---

### Post by porphyry5 on 2011-04-16
> **scott-ian said:**
> An easy way would be to go into System --> Administration --> Users and Groups, select the user, click "advanced setings" and under the "User Privileges" tab, check "Mount user-space filesystems."  You would have to do this individually for each user, but I think it would work.
I guess I have to use the difficult option, when I click Advanced Settings the button activates, but there is no response.

---

