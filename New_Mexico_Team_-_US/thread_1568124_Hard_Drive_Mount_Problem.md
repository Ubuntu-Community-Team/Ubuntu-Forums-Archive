---
title: "Hard Drive Mount Problem"
date: 2010-09-04
forum: New Mexico Team - US
---

### Post by xzing on 2010-09-04
I have installed a new hard drive to my Ubuntu 9.10 system.  Before I upgrade and mess everything up (again) I would like to get a solution to my problem.  Please help this has been plaguing me for quite some time.

I tried mounting the new hard drive to a folder that I created /media/data.  When I start my machine I see the drive listed under **Places** and I can click on it and I get a message asking me for my password.  After I type in the password I can get to all of the folders no problem.  But I can never just get the drive to mount.  It is listed as /dev/sdb.  I edited the fstab file with the following line.

/dev/sdb1 /media/data ext3 defaults 0 2 

This does not seem to work. I can tell you that when I go to **System** -> **Administration** -> **Disk Utility** the program tells me the drive is not partitioned.  Could this be my problem? 

Lastly, so you know all the details, when I do click on the drive and enter my password the drive shows up under /media.  But the folder/drive name is the UUID number of the drive.

Sorry for the length of this post I just wanted to give all the info I could.  But, I am really stuck and frustrated here.  Any help would be good at this point!

Regards,
Xzing

---

### Post by Morbius1 on 2010-09-04
> Lastly, so you know all the details, when I do click on the drive and  enter my password the drive shows up under /media.  But the folder/drive  name is the UUID number of the drive.
It will usually show up with the UUID because the line you have in fstab is being ignored and it's mounting it through the default process.

A proof of that is this observation:
>  When I start my machine I see the drive listed under **Places** and I  can click on it and I get a message asking me for my password.  After I  type in the password I can get to all of the folders no problem.If it was properly mounted in fstab you would never be asked for a passowrd.

Why not post the output of the following command so we can see what's up:
```
sudo blkid -c /dev/null
```

---

### Post by GrammatonCleric on 2010-09-05
Also are you sure that the drive is formated ext3 and not ext4?  If the drive is formated ext4 your fstab entry will fail to mount the drive to the mount point.

-GC

---

### Post by mvelte54 on 2010-09-05
I too am having the same problem. I will be interested in the out come. Both drives are ext3.

---

