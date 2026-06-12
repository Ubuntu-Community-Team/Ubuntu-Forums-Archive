---
title: "permissions permissions what to do?"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by pstevenson83 on 2009-12-17
If one doesn't have permission to change the permissions, how is  it ever to be done? I am the owner/admin/ and i know the password. but i still don't have permission to move or look into some folders like songbird (which i have downloaded but was never able to run btw)

---

### Post by bodhi.zazen on 2009-12-17
use sudo

sudo chown 
sudo chmod

Thes commands will fail, however, it you are trying to set permissions on a FAT or NTFS partition. Windows file systems do not support permissions , and so permissions are set when you mount the partition.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

