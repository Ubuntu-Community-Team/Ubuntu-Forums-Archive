---
title: "Map a NAS drive"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by jmumby on 2010-12-30
How would you map a drive so it always mounts at start up as drive letter? I have a nas drive and Im having a bit grief trying to get it to work with Luckbackup, or anything that doesn't like smb shares.

---

### Post by anystupidname1 on 2010-12-30
This should answer your question:
[http://ubuntuforums.org/showthread.php?t=509931](http://ubuntuforums.org/showthread.php?t=509931)
I would recommend NFS over SMB if that is an option in your scenario:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) (skip to the client section)

---

### Post by perspectoff on 2010-12-30
In Dolphin (Kubuntu), and perhaps in Nautilus (Ubuntu), you can add a network location and specify the network address of the NAS. That keeps it mounted, at least when accessing it from those file managers.

Otherwise, use the solution in the thread specified in the previous post, which entails editing the /etc/fstab file.

---

### Post by kellemes on 2010-12-31
This works for me with cifs.. in /etc/fstab.
```
//location   /mnt/location    cifs user, uid=1000, iocharset=utf8, rw, suid, credentials=/location/file.txt  0  0  
```

(create /location/file.txt with username/password)

---

### Post by jmumby on 2011-01-02
My WD World book supports NFS. I followed [this guide]("http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html") and it is working like a charm

---

