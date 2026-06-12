---
title: "can't find second hard drive"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by dierubikdie on 2009-01-17
Yeah I am most definitely a noob in the linux world, and I'm having a few problems. First of all, I installed ubuntu 8.10 desktop on my laptop, and now it can't seem to find my second hard drive. I have a sony vaio with two 100GB hard drives. Also, I can't figure out how to get it to recognize any memory sticks or usb flash drives. I guess I should find some drivers? Help this poor noob...

---

### Post by taurus on 2009-01-17
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by dierubikdie on 2009-01-17
dierubikdie@Brady-VAIO:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x608d7d9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         891     7150592   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         891       12162    90533144    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf066a1a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11661    93666951   83  Linux
/dev/sdb2           11662       12161     4016250    5  Extended
/dev/sdb5           11662       12161     4016218+  82  Linux swap / Solaris

dierubikdie@Brady-VAIO:~$ sudo blkid
/dev/sda1: UUID="DECAACEDCAACC35F" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="5C346468346446DC" LABEL="VISTA" TYPE="ntfs" 
/dev/sdb1: UUID="5c167a05-30e2-4dcf-b688-7f013514af26" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="d25011a5-ca5c-434f-bdb9-d5e06f463db6" 

dierubikdie@Brady-VAIO:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5c167a05-30e2-4dcf-b688-7f013514af26 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=d25011a5-ca5c-434f-bdb9-d5e06f463db6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

dierubikdie@Brady-VAIO:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              88G  2.8G   81G   4% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  108K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  128K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda2              87G   47G   40G  55% /media/VISTA
/dev/sda1             6.9G  6.0G  904M  88% /media/Recovery

---

### Post by taurus on 2009-01-17
> **dierubikdie said:**
> dierubikdie@Brady-VAIO:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x608d7d9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         891     7150592   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         891       12162    90533144    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf066a1a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11661    93666951   83  Linux
/dev/sdb2           11662       12161     4016250    5  Extended
/dev/sdb5           11662       12161     4016218+  82  Linux swap / Solaris

dierubikdie@Brady-VAIO:~$ sudo blkid
/dev/sda1: UUID="DECAACEDCAACC35F" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="5C346468346446DC" LABEL="VISTA" TYPE="ntfs" 
/dev/sdb1: UUID="5c167a05-30e2-4dcf-b688-7f013514af26" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="d25011a5-ca5c-434f-bdb9-d5e06f463db6" 

dierubikdie@Brady-VAIO:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5c167a05-30e2-4dcf-b688-7f013514af26 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=d25011a5-ca5c-434f-bdb9-d5e06f463db6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

dierubikdie@Brady-VAIO:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              88G  2.8G   81G   4% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  108K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  128K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
**[COLOR="Blue"]/dev/sda2              87G   47G   40G  55% /media/VISTA[/COLOR]**
/dev/sda1             6.9G  6.0G  904M  88% /media/Recovery

Looks like you have your windows partition, /dev/sda2, already mounted to /media/VISTA.  /dev/sda1 (/media/Recovery) is your recovery partition in case you need to reinstall vista since you don't have a vista disc with your laptop.

---

### Post by dierubikdie on 2009-01-17
thanks for the clarification! so how do I get my memory stick and usb drives to work?

---

### Post by taurus on 2009-01-17
Normally, Ubuntu would automount it when you plug it in UNLESS you didn't use the safely remove hardware option (little icon in the bottom right) when you used the USB stick or drive while in windows.

However, you can still mount it by hand from a terminal if you wish.  Plug one in and then post the outputs of these two commands from a terminal.

```
sudo fdisk -l
df -h
```

---

### Post by dierubikdie on 2009-01-17
dierubikdie@Brady-VAIO:~$ sudo fdisk -l
[sudo] password for dierubikdie: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x608d7d9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         891     7150592   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         891       12162    90533144    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf066a1a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11661    93666951   83  Linux
/dev/sdb2           11662       12161     4016250    5  Extended
/dev/sdb5           11662       12161     4016218+  82  Linux swap / Solaris
dierubikdie@Brady-VAIO:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              88G  6.4G   78G   8% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  108K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  256K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda2              87G   47G   40G  55% /media/VISTA
/dev/sda1             6.9G  6.0G  904M  88% /media/Recovery

---

