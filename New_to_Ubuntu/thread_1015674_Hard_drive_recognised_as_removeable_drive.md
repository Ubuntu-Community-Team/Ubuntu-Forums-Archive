---
title: "Hard drive recognised as removeable drive?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Konj on 2008-12-19
One of my partitions is acting weirdly. It seems to be mounted at startup, but Nautilus doesn't show it as such and in the "Places" panel, it shows as not mounted. However, it is present in /media and accessible from there. If I try to mount it in Nautilus, it effectively mounts the drive twice. When I unmount it in Nautilus, it comes up with this message:

[IMG]http://i437.photobucket.com/albums/qq95/Konjury/Untitled.png[/IMG]

What could be wrong? Thanks in advance.

---

### Post by Michael.Godawski on 2008-12-19
> **Konj said:**
> One of my partitions is acting weirdly. It seems to be mounted at startup, but Nautilus doesn't show it as such and in the "Places" panel, it shows as not mounted. However, it is present in /media and accessible from there. If I try to mount it in Nautilus, it effectively mounts the drive twice. When I unmount it in Nautilus, it comes up with this message:

[IMG]http://i437.photobucket.com/albums/qq95/Konjury/Untitled.png[/IMG]

What could be wrong? Thanks in advance.

hi

can you please post the outputs of these terminal commands:

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Konj on 2008-12-19
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004434d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           13055      107566   759167640    5  Extended
/dev/sda2   *           1       13054   104856223+  83  Linux
/dev/sda5           13055       13576     4192933+  82  Linux swap / Solaris
/dev/sda6           13577       65793   419433021   83  Linux
/dev/sda7           65794      107566   335541591   83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=353f9149-d10b-4fa6-b88e-7617f60b65aa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=079b5337-5c8d-4807-8e6a-79fe0e7f90a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Filesystem            Size Used Avail Use% Mounted on
/dev/sda2              99G  6.1G   88G   7% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  212K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1010M   1% /dev
tmpfs                1012M  664K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6             394G   71G  304G  19% /media/Media
/dev/sda7             315G   55G  245G  19% /media/Torrents


Thanks.

---

### Post by madverb on 2008-12-19
You need to add the other partition to your fstab file.

---

### Post by Konj on 2008-12-19
I'm sorry? It doesn't do this with my other partition, which is also absent from the fstab file. So it should be something else which is casuing it to going awry. Correct me if I'm wrong.

---

### Post by madverb on 2008-12-19
Just add it to fstab and see if it resolves the problem. If it does not then we can look into other fixes.

---

### Post by Konj on 2008-12-19
Would the following be correct?

/dev/sda6	/media/Media	ext3	0	0
/dev/sda7	/media/Torrents	ext3	0	0

I am unsure if the mountpoint should be /media or /mnt, and what to put for the options.

---

### Post by madverb on 2008-12-19
you can mount it where ever you like. /media is the standard these days though.

You also have to remember to create the directories under the /media folder.

---

