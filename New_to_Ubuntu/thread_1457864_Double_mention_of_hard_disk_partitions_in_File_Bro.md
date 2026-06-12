---
title: "Double mention of hard disk partitions in File Browser (Nautilus)"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by S. Cornelissen on 2010-04-19
Dear all,

I have an Ubuntu system with one hard disk divided in four partitions: one for the File System, one as swap and two that I use as data storage. Let's call these two data disks One and Two.

When I boot my PC and open Nautilus (or for that matter look in the Places menu), disks One and Two both show up twice. Once fully mounted (with the hard drive icon left and the Eject button right to them) and once with a different icon (looks a bit like a floppy or CD drive...).

The first instances are fully accessible and functional. The second are not, when I click them they say:

Unable to mount One
mount: according to mtab, /dev/sda4 is already mounted on /media/One
mount failed

I don't need these instances. **How can I get rid of them?**

Right clicking gives no delete option. 

I hope you understand the problem and can help with solutions.

Cheers,
Stijn

---

### Post by Skorzen on 2010-04-19
Please post the output of your /etc/fstab file.

To do that:
```
cat /etc/fstab
```

---

### Post by S. Cornelissen on 2010-04-19
> **Skorzen said:**
> Please post the output of your /etc/fstab file.

To do that:
```
cat /etc/fstab
```

Hmmm, in a lousy format, hope this works:

proc                                       /proc            proc         defaults               0  0  
UUID=9982d6d8-04a5-4bc8-9ec3-d9dc33e3cceb  /                ext4         errors=remount-ro      0  1  
UUID=793518d1-a77b-451e-a67b-32ac09a3c701  /media/One     ext4         owner                  0  2  
UUID=f4aa13e3-4e8e-401a-b7d7-c94c82e29641  /media/Two  ext4         owner                  0  2  
UUID=c3d738e2-0100-4bbf-9555-65c7b0f5320b  none             swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8  0  0

---

### Post by S. Cornelissen on 2010-04-22
To further clarify the issue, I have attached a screenshot of the Nautilus/Places window. 

The top instances of Stijn and ZinInZin work, the bottom two do not.

---

### Post by oldfred on 2010-04-22
The symbols indicate that is the mounted version. 

I mount something partitions but because I do not mount them in /media or /home I do not see them. I then link to the data that I mounted.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by Morbius1 on 2010-04-22
Could be this: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

To work around your issue, you need to change the syntax like this:

[COLOR=Blue]/dev/disk/by-uuid/[/COLOR]793518d1-a77b-451e-a67b-32ac09a3c701  /media/One     ext4         owner                  0  2

---

### Post by S. Cornelissen on 2010-04-23
Thanks a lot, the trick of removing UUID and adding /dev/... indeed solved the issue. Hopefully this can be fixed in future versions of Ubuntu, because it was annoying and I prefer not to manually code stuff to fix things! ;-)

---

