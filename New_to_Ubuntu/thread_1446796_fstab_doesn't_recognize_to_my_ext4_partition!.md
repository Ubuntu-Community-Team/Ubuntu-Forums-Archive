---
title: "fstab doesn't recognize to my ext4 partition!"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-04-04
in order to automatically mount my partition i have add the following line to fstab file:
 
[PHP]/dev/sda3       /media/3        ext4 users,auto,exec,utf8 0       0[/PHP]

the system should mount it on the start up,but this didn't happen!!!

any help??

---

### Post by falconindy on 2010-04-04
You have conflicting and somewhat strange options. Replace with: "defaults,relatime"

---

### Post by sandyd on 2010-04-04
> **MBG1987 said:**
> in order to automatically mount my partition i have add the following line to fstab file:
 
[PHP]/dev/sda3       /media/3        ext4 users,auto,exec,utf8 0       0[/PHP]

the system should mount it on the start up,but this didn't happen!!!

any help??
a) you should be using UUIDs, not "/dev/sda3"
you can find the UUID through 
```

blkid
```

once you get the UUID, replace "/dev/sda3" with
```

UUID=*uuid_you_just_found*
```

b) does the mount point exist?
as in, does /media/3 exist.

c)
can you do ```

sudo mount -a
```

and post the output.

**edit -> see above post**

---

### Post by MBG1987 on 2010-04-06
> a) you should be using UUIDs, not "/dev/sda3"
  you can find the UUID through 
       

      
  once you get the UUID, replace "/dev/sda3" with      i already mounted the ntfs partition and work fine:
[PHP]/dev/sda2       /media/4        ntfs users,auto,exec,utf8 0       0[/PHP]> b) does the mount point exist?
  as in, does /media/3 exist.
 yep
 
 > c)
 and post the output.  nothing happened with "sudo mount -a" !!

---

### Post by sisco311 on 2010-04-06
utf8 is not a valid mount option for an ext4 partition:
```
/dev/sda3   /media/3   ext4    relatime    0       2
```

---

### Post by MBG1987 on 2010-04-06
it works, thank u

---

