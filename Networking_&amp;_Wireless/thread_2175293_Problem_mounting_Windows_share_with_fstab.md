---
title: "Problem mounting Windows share with fstab"
date: 2013-09-18
forum: Networking &amp; Wireless
---

### Post by kathrync on 2013-09-18
I am trying to mount two network drives permanently with fstab in Ubuntu 13.04.  The lines in fstab are as follows(server names edited for privacy):
```
//SERVER1/SSD_Home_Data_X/user    /local/net/home    cifs    credentials=/home/kathryn/.credentials,workgroup=campus,auto,uid=1000,gid=1000    0   0
//SERVER2/SSD_Dept_Data_D/MVL/MVLPublic    /local/net/MVLPublic    cifs    credentials=/home/kathryn/.credentials,workgroup=campus,auto,uid=1000,gid=1000    0   0

```

The first one mounts fine, but the second doesn't. If I run sudo mount -a, I get the following error:  ```
mount error(2): No such file or directory. Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
``` I can however mount both from nautilus using the server addresses and paths to the share cut and pasted from the fstab file so I know the address for the one that isn't working is correct.  

I don't have any control over the shared drives, but I wanted to check I wasn't doing anything silly at my end before I go and annoy the people who do control the shares!

Any thoughts?

---

