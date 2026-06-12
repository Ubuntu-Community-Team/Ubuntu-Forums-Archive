---
title: "ext4 vs. NTFS, what to use?"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by kkpickel on 2010-12-05
I installed Ubuntu 10.10 yesterday to my laptop, I've had some issues with my touchpad and do not have access to some folders so I can edit them to get my touchpad to work.  I'm wondering if it's because my hard drive partition in Windows, formatted my filesytem by default to NTFS, my question is would it make a difference if my filesystem was ext4 (or earlier)?

---

### Post by llamabr on 2010-12-05
[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+read+write+ntfs&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+read+write+ntfs&ie=utf-8&oe=utf-8)

It's not too likely that it's an ntfs problem, though the above link will help.  It's more likely to be permissions.  Copy paste what you're trying to do, as well as the error msg you get.

---

### Post by Morbius1 on 2010-12-05
There is a 117.62% chance that I'm misinterpreting your post but do you mean you installed Linux onto a an NTFS partition?

First I didn't even know that was possible but if it is it won't work. There needs to be a segregation of directories by owner with different permissions for specific files. NTFS can't do that.

Are you sure this isn't a Wubi install?

---

### Post by kkpickel on 2010-12-05
I installed Ubuntu 10.10 to a NTFS partition, it's possible, I just checked my partition type in Disk Utility and it says my partition type is NTFS.  

I could totally be doing something wrong, I'm new to Ubuntu and to partitioning hard drives so I'm up for any suggestions on how to make it right.

---

### Post by kkpickel on 2010-12-05
OK...I just looked up Wubi install and YES it's a Wubi install...

---

### Post by CharlesA on 2010-12-05
Mmk. Wubi install, see below:

EDIT: The Ubuntu install is installed on an ext4 partition by default. If you want to share files between the Wubi install and Windows, you'd have to mount the Windows partition (or create a separate partition) and copy the files over.

---

### Post by Morbius1 on 2010-12-06
> **CharlesA said:**
> Mmk. Wubi install, see below:

EDIT: The Ubuntu install is installed on an ext4 partition by default. If you want to share files between the Wubi install and Windows, you'd have to mount the Windows partition (or create a separate partition) and copy the files over.
I know nothing about Wubi but aren't the Windows partitions already mounted ( or at least accessible ) at /host and /media on the Ubuntu install?

The bigger problem seems to be this:
> **kkpickel said:**
> I've had some issues with my touchpad and do not have access to  some folders so I can edit them to get my touchpad to work. 
Not sure if this is because it requires root access or even with root access it's still not accessible. Need clarification.

If you're trying to edit some config file owned by root then you need to launch gedit as root:
```
gksu gedit
```

---

### Post by diablo75 on 2010-12-06
> **kkpickel said:**
> OK...I just looked up Wubi install and YES it's a Wubi install...

Wubi is horrible (IMHO).  I would back up any info you have in your home folder, uninstall the Wubi version of Ubuntu via Windows>Control Panel>Add/Remove Programs (to free up hard drive space), then install fresh from a Live CD.  When it gets to the partitioning portion of the setup, tell it you want to "Install Alongside Another OS" or equivalent.

If you can't use a CD, perhaps you can boot from a USB flash drive.

I've had problems with Wubi in the past that, simply put, never happened on a "real" install.  Wubi doesn't repartition the hard drive at all.  Instead it installed Ubuntu inside of a folder on your NTFS partition simply called Ubuntu, and then uses a special boot-loader to trick Ubuntu into thinking it's sitting on a real, separate partition.  It just doesn't work as good as it should.  I'm surprised these sorts of issues still appear (I would expect bugs like this to be easy to reproduce and fix, but not many people... and even fewer developers, use Wubi).

ext4 is the way to go.

---

### Post by CharlesA on 2010-12-06
> **Morbius1 said:**
> I know nothing about Wubi but aren't the Windows partitions already mounted ( or at least accessible ) at /host and /media on the Ubuntu install?

I'm not sure, since I've always done pure dualboot if I want to run another OS, never done a Wubi install.

---

### Post by philinux on 2010-12-06
Just for info.

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#Limitations](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#Limitations)

Also read the developers comments.
> Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. 
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

---

