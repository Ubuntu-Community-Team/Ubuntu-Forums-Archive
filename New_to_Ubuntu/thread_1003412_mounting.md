---
title: "mounting"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by sameer.india on 2008-12-06
my ntfs partitions aren't mounted when I log in to my account.
I have to mount them separately everytime.
How can I mount them forever

---

### Post by vanadium on 2008-12-06
You can mount them "forever" (=automatically during startup) by including a line for these partitions in /etc/fstab. Search for "ubuntu mount ntfs /etc/fstab". If this remains difficult for you, open the terminal and post the output of the following commands here in the forum

```

cat /etc/fstab
sudo fdisk -l

```

The second comman will require you to enter your login passwoord because you are acting as root.

---

### Post by sameer.india on 2008-12-06
sameer@Sameer-laptop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=80868411-3784-4dbe-9e5d-a44c72e81747 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=7050f0fe-da93-4e31-8b32-4967c227b19d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sameer@Sameer-laptop:~$ sudo fdisk -l
[sudo] password for sameer: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003ae8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3576    28724188+   7  HPFS/NTFS
/dev/sda2            3577       16659   105089197+   7  HPFS/NTFS
/dev/sda3           16660       19424    22209862+  83  Linux
/dev/sda4           19425       19457      265072+  82  Linux swap / Solaris

---

### Post by lovelyvik293 on 2008-12-06
Just add the /dev/sda1 in the fstab like


```
/dev/hda1 /mnt/windows ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

---

### Post by vanadium on 2008-12-06
Essentially, all you need to do is add a line for the partition in /etc/fstab like

```

/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

```

I adapted this from the example here
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[edit]I see someone was faster. One extra note: the mount point (/media/windows in my example, /mnt/windows in the example of lovelyvik293, must exist. Better follow his line, because it already regulates the permissions of the drive as well.

Create the mount point, which is just a directory, using a nautilus Window with root permissions: "gksudo nautilus" in the terminal (close that nautilus window as soon as you are done)

---

