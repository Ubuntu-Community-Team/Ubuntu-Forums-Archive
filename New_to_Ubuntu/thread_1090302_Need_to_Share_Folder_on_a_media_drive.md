---
title: "Need to Share Folder on a /media/ drive"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Chrissd on 2009-03-08
Hi, I need to share a folder on /media/, but it won't change the permissions of the folder when I "sudo chmod o+xr /media/250GB/Folder".

The chmod doesn't return any faults, but with "ls -ld /media/250GB/Folder" I get: drwxrwx--- 1 root plugdev 4096 2009-03-01 20:32 /media/250GB/Folder.

I also tried through the GUI using sharing options, and the fails too.

I'm a complete Ubuntu newbie, please help.

---

### Post by blueridgedog on 2009-03-08
If the drive mounted under /media/250GB is fat32 or NTFS, then the permissions can be adjusted for individual files or sub-folders, the entire drive is mounted with a given user/group at mount time.

---

### Post by Nepherte on 2009-03-08
I always set permissions for fat/ntfs drives in my /etc/fstab file. You can do it with these options added to the fat hard disk entry:
```
uid=1000,gid=100,dmask=027,fmask=137
```
uid = owner (1000 = first created user, i.e. my account)
gid = group owner (100 = group users)
dmask = directory permissions (027 = 750 permissions, just invert each number: 7 - digit)
fmask = file permissions (137 = 640 permissions, see above)
The settings will apply for each directory and file on that share.

---

