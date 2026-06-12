---
title: "fstab to edit ext4 used for general storage"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by nitstorm on 2010-04-10
i have a partition to store my music and all but i need to add it to my fstab in order to use it . how do i make a permanent change by putting the partition in fstab so that it gets mounted automatically everytime i boot

here is an output of fdisk -l if u need it 
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe603e603

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2549    20472656+  83  Linux
/dev/sda2            2612       19456   135307432    5  Extended
/dev/sda5            2612        5222    20972826   83  Linux
/dev/sda6            5223        7833    20972826   83  Linux
/dev/sda7            7834       10444    20972826   83  Linux
/dev/sda8           10445       10705     2096451   82  Linux swap / Solaris
/dev/sda9           10706       10836     1052226   83  Linux
/dev/sda10          10837       19456    69240118+  83  Linux

```
the device that needs to be added to fstab is /dev/sda10

---

### Post by nitstorm on 2010-04-10
Anybody????

---

### Post by nitstorm on 2010-04-10
edited the fstab by looking at this thread
[http://ubuntuforums.org/showthread.php?t=1145596](http://ubuntuforums.org/showthread.php?t=1145596)

but then now i don't have any permissions to the folders inside that
f.y.i : i changed the permissions of the folder in the partition but then i am unable to access the sub-folders now

also is there a command that changes the permissions of the folders and all the files within it recursively?

---

### Post by nitstorm on 2010-04-10
Did some digging and found the command myself

```

chmod 777 -R DIRECTORYNAME

```

Solved this thread on my own thanks to links, cheers guys :)

---

### Post by ackley on 2010-04-10
I don't mind, but I know some people frown upon people wanting immediate responses on their forum posts. If you're looking for a quick response, sometimes an IRC chat is better suited.

But, to answer your question, how to apply permissions recursively, use the -R option. 

So it'd be like

chmod -R 777 /path/to/dir

---

### Post by ackley on 2010-04-10
> **nitstorm said:**
> 

```

chmod 777 -R DIRECTORYNAME

```

Or that, too. I just woke up.

---

### Post by nitstorm on 2010-04-10
> **ackley said:**
> Or that, too. I just woke up.
LOL, no issues...

---

