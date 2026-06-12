---
title: "delete vista folders"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by hammad1337 on 2009-02-23
I have a partition which used to contain Windows Vista. I deleted windows from it, but could not (and cannot) delete these folders:
 -> Documents and Settings
 -> ProgramData
 -> Users
When I try to delete them, it gives me this:
```

$ sudo rm -r /media/DATA/ProgramData
[sudo] password for ######: 
rm: cannot remove directory `/media/DATA/ProgramData/Application Data': Operation not supported
rm: cannot remove directory `/media/DATA/ProgramData/Desktop': Operation not supported
rm: cannot remove directory `/media/DATA/ProgramData/Documents': Operation not supported
rm: cannot remove directory `/media/DATA/ProgramData/Favorites': Operation not supported
rm: cannot remove directory `/media/DATA/ProgramData/Start Menu': Operation not supported
rm: cannot remove directory `/media/DATA/ProgramData/Templates': Operation not supported
$

```

The ntfs partition is mounted as rw.
Also, I can modify any other files/folders on this partition.

I don't want to format the partition as it contains important data as well. And I don't have n extra hard-disk/partition to transfer that data too.

Any thoughts?

---

### Post by carml on 2009-02-23
Do you have full access to those directories via Linux, or are you trying to do that via Windows?

---

### Post by hammad1337 on 2009-02-23
I have tried to delete them though windows, but I can't.
I m trying to delete it from linux.

Here are the permissions:

[code]
$ ls -l /media/DATA/
drwxrwxrwx 1 root root        0 2008-12-13 04:58 Documents and Settings
drwxrwxrwx 1 root root     4096 2009-02-13 15:47 ProgramData
drwxrwxrwx 1 root root     4096 2009-02-13 15:48 Users
$
[code]
(Showing only the relevant entries.)

---

### Post by carml on 2009-02-23
Sorry, I use too much the GUI,did you give full access to windows from linux?
Maybe you should install something called ntfs????.deb, sorry it's a long time I saw the right name of this package.:)

---

### Post by theozzlives on 2009-02-23
```
sudo rm -rf documents\ and\ Settings
```
from Linux should do it, but that's where Windows keeps it's data. You sure you wanna delete that one?

---

### Post by Le-Dart on 2009-02-23
Were you able to remove all the other Windows files this way? Do you have ntfs-3g installed?

---

### Post by mikechant on 2009-02-23
I think your problem relates to a NTFS filesystem feature called 'reparse points' (in this case I believe, a specific type of reparse point called a 'junction point'. The directories you list are special ones which have been relocated/renamed in Vista (compared to XP) and use the reparse point feature to make this move transparent (i.e. both old and new filenames/paths will work). 
As per the NTFS-3G FAQ here: [http://ntfs-3g.org/support.html#filedelete](http://ntfs-3g.org/support.html#filedelete)

Reparse points are not fully supported in the current version of the NTFS-3G driver, so I guess you either need to try the (presumably still experimental) advanced NTFS-3g driver mentioned in the FAQ above (looks like you need to build it from source - no .deb package), or hook this drive up to another Vista system to delete these items.

However, are you sure that you don't have the means to backup the data you *do* want from this partition? How big is it? How much free space do you have in your Linux partition/s? Don't you have any backup devices - DVD writer, external hard drive, external flash drive? Or could you borrow something? that would make it nice and easy - back up the stuff you want and reformat the partition etc.

---

### Post by hammad1337 on 2009-02-23
rm -rf did not work.
I have ntfs-3g package installed.

I thought this might e helpful in diagnosis:
```

 $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=90811b7b-ba69-4efe-bd35-9e46b1067ff8 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda7	/media/DATA	ntfs	umask=0		0	0
/dev/sda1	/media/disk	ntfs	umask=0		0	0
$

```
should I change something in my fstab?

---

### Post by carml on 2009-02-23
To complete previous suggestions I checked the package installed with ntfs in the name: 

libntfs-3g23 and ntfs3g.
Check if these are installed,also as suggested,I didn't notice before my bad,you have to code rm -R to remove folder on Linux,maybe it works also for Windows .
Tell us your progresses :).

---

### Post by tarps87 on 2009-02-23
I think mikechant's post identifies the problem, the solution being to use the advanced version if NTFS-3G.
Another solution may be, if you have space would be to create a second partition on that drive copy across the data you want and extend the new partition. This is risky and you could loose all or data so should be a last resort method.

mikechant's post actual explains so problem I had when trying to recover a friends vista pc.

---

### Post by hammad1337 on 2009-02-23
Thank you all for your prompt help. :)

I think I'll hook this HD to a friend's PC, and delete these folders from there.

Sadly, I don't have a another large hard-disk to backup ~120 GB of data I've accumulated.

---

### Post by carml on 2009-02-23
> **tarps87 said:**
> I think mikechant's post identifies the problem, the solution being to use the advanced version if NTFS-3G.
Another solution may be, if you have space would be to create a second partition on that drive copy across the data you want and extend the new partition. This is risky and you could loose all or data so should be a last resort method.

mikechant's post actual explains so problem I had when trying to recover a friends vista pc.

+1 I looked again the path of the folder you want to remove,mikechant maybe nailed the problem.
If it can help,me too I have more than a partition under Vista: C:\ and D:\,with the first in use for programs and the second one for backup purpose.:)

---

