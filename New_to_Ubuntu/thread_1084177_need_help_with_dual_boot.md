---
title: "need help with dual boot"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by 440corbon on 2009-03-01
I was using a wubi install and everything was working for me. So I decided to just do a regular install. I didn't get my boot menu and "xp" auto booted. So I tried install again. Thinking My bootloader didn't install. It turns out I have to have my live cd in to boot. Here is my system info

user@user-desktop:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03dd7234

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3580    28756318+  83  Linux
/dev/sda2            3581        3739     1277167+   5  Extended
/dev/sda5            3581        3739     1277136   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f1764e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14432   115925008+   7  HPFS/NTFS
/dev/sdb2           14433       38913   196643632+   f  W95 Ext'd (LBA)
/dev/sdb5           14433       14824     3148708+  83  Linux
/dev/sdb6           14825       17365    20410551   83  Linux
/dev/sdb7           38158       38913     6072538+  82  Linux swap / Solaris
/dev/sdb8           17366       37401   160939138+  83  Linux
/dev/sdb9           37402       38157     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order
edmund@edmund-desktop:~$ blkid
/dev/sda5: UUID="855f17de-1a26-469e-8846-f34959875a33" TYPE="swap" 
/dev/sdb1: UUID="FA7057C770578971" LABEL="DRV5_VOL1" TYPE="ntfs" 
/dev/sdb5: UUID="9514c81d-4821-4b73-8825-de1450cf8373" TYPE="ext2" 
/dev/sdb6: UUID="745b2d2d-05b6-4745-b605-dcef39025044" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="bd16dbf5-0be5-428e-8929-f481fe0bb7d7" TYPE="swap" 
/dev/sdb8: UUID="2d4d9fcc-f4c9-46a7-ab19-d68890c1405a" TYPE="ext3" 
/dev/sdb9: UUID="e04aa204-b633-4c32-a76d-6a78a61a2dfb" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
user@user-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb8
UUID=2d4d9fcc-f4c9-46a7-ab19-d68890c1405a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb9
UUID=e04aa204-b633-4c32-a76d-6a78a61a2dfb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
user@user-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb8             152G   18G  127G  12% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  100K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.9M 1010M   1% /dev
tmpfs                1013M  128K 1012M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-11-generic/volatile
user@user-desktop:~$ id
uid=1000(user) gid=1000(user) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(edmund)
Note: I am using the 350gig drive the 30gig drive won't boot(error 15/17)

Any help would be much appreciated.

---

### Post by abhiroopb on 2009-03-01
I have written a guide on how to fix GRUB (the ubuntu boot loader) so that you are able to use it to load Ubuntu after XP wipes it out.

Have a read, and feel free to post comments.

[http://ubuntuextreme.blogspot.com/2008/12/how-to-re-install-grub-after-windows_17.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-re-install-grub-after-windows_17.html)

---

### Post by 440corbon on 2009-03-01
Thank you.
 I installed xp first. would the live cd have still installed grub to the first partition of that drive?

---

### Post by 440corbon on 2009-03-01
I believe the issue has been solved. I reset the grub to point to another section and it worked. Don't know why it didn't work the first time though.

---

