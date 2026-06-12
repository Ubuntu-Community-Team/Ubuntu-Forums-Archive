---
title: "Finding Space Used on SSD"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by ambleside on 2011-04-11
mnt point for SSD is /

I can't figure out using Disk Usage Analyzer or other tools exactly which files are on the SSD vs. other disks.  I can see used/capacity in gparted but it doesn't show me me which files are consuming the space.

I've moved home off the SSD,  all my VDI's, but I still find little things cropping up (today it was a new snapshot disk for a vm - I had moved the disk itself off but the directory must still be on the ssd and it put a 20gb snapshot on the SSD.).  And one of these days I'm going to run out of app install space..

Here is my FSTAB:
[INDENT][SIZE=1]UUID=75137c1f-4f1e-4c3c-9492-54398fab2326  none           swap  sw                   0  0  
/dev/sdb6                                  /mnt/data      ext4  defaults             0  0  
/dev/sdb1                                  /media/sdb1    ntfs  defaults             0  0  
/dev/sdb2                                  /mnt/win7      ntfs  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0 
/dev/sdb3                                  /mnt/crestron  ext4  defaults             0  0  

UUID=4b2be799-4bdc-41f8-877a-e9d69287bedc / ext4 errors=remount-ro,user_xattr 0 1

[/SIZE][/INDENT]Thanks,

Aaron

---

### Post by seawolf167 on 2011-04-11
Take a look at

```
man du
man df
```

to see file/folder sizes in your current directory for example (in human-readable format)

```
du -h
```

---

