---
title: "nfs mounting a mounted folder"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by jamx on 2008-05-01
Forgive the title, its hard to sum this up in a few words.

Here is my problem:

I have a folder (/share) and in there I mount three file systems.
```
/share/raid1.5TB (/dev/mapper/nvidia_dfggfcba ext3)
/share/raid500GB (/dev/mo0 ext3)
/share/120GB (/dev/sdf1 ext3)
```

All three mounts work fine on the machine and via samba etc...

When I try and mount them using nfs, I can navigate to the /share folder and I can see each folder inside, but when I try and go into any of them, I just see a blank folder and I can't read or write anything.

If I unmount the volumes, nfs will let me write to the empty mountpoints.

nfs is working as I have /home shared and I can read / write anything withing there.

My export lines are (/etc/exports)
```
/share  192.168.1.0/255.255.255.0(rw,async,no_root_squash)
/home   192.168.1.0/255.255.255.0(rw,async,no_root_squash)
```

```
jay@wildfire:/share$ ls -l
total 12
drwxrwxrwx 8 jay jay 4096 2008-05-01 13:41 120GB
drwxrwxrwx 5 jay jay 4096 2008-05-01 13:21 raid1.5TB
drwxr-xr-x 2 jay jay 4096 2008-05-01 13:53 raid500GB
```


I'm using 8.04 server.

Any ideas? Thanks. Jay.

---

