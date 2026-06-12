---
title: "Trying Hibernation"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-08
I try to hibernate, the screen goes blank, says something about read/write error, then asks my password and WEP key. The system load average goes to 100% and slowly goes back down. I have a 4 GB swap (2 GB RAM).

hopefully the following proves helpful:
```
ozzie@ozzie-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2014        492       1521          0         20        199
-/+ buffers/cache:        272       1742
Swap:         4598          0       4598
ozzie@ozzie-laptop:~$ sudo fdisk -l
[sudo] password for ozzie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       15633   115089660   83  Linux
/dev/sda3   *       15634       18935    26523315    7  HPFS/NTFS
/dev/sda4           18936       19457     4192965    5  Extended
/dev/sda5           18936       19457     4192933+  82  Linux swap / Solaris
ozzie@ozzie-laptop:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	515796	0	100
/dev/sda5                               partition	4192924	0	-1
ozzie@ozzie-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
/dev/sda2 /home ext3 nodev,nosuid 0 2
# Windows Partition
/dev/sda3 /windows ntfs 0 0
# DVD Writer
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ozzie@ozzie-laptop:~$ 

```

---

