---
title: "ntfs in xubuntu"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by computer wizard on 2009-01-25
i have had trouble with windows in the past and have decided to install xubuntu. but there are some files on my ntfs hadr drive i need to access here is the config of my computer,

2 hdd's
hdd0 part0 xubuntu
hdd1 part0 ntfs, windows xp sp2
2cd roms
1 floppy <-- Broken.

can somebody please help i have a resume on that hdd and i need it fast.

---

### Post by sisco311 on 2009-01-25
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

or
open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
mount
```

Do you want to mount it at boot time or just once?

---

### Post by computer wizard on 2009-01-25
here is the entire termanal window, and i would like to access it at boot also


-------------------------------------
billy@billy-desktop:~$ sudo fdisk -l
[sudo] password for billy: 

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf050f050

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x689e689e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.
billy@billy-desktop:~$ 
----------------------------------------------

---

### Post by computer wizard on 2009-01-25
> **sisco311 said:**
> [http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

or
open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
mount
```

Do you want to mount it at boot time or just once?
ok so i messed up on my first try but after fixing a screen error (cat was playing with the cord) i typed in the entire thing and got 

----------------------------
billy@billy-desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf050f050

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x689e689e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.
billy@billy-desktop:~$ blkid
billy@billy-desktop:~$ /ect/fstab
bash: /ect/fstab: No such file or directory
billy@billy-desktop:~$ cat /ect/fstab
cat: /ect/fstab: No such file or directory
billy@billy-desktop:~$ cat /ett/fstab
cat: /ett/fstab: No such file or directory
billy@billy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=275abd45-cb06-4cee-9b4f-132cd5481bac /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c86d109c-d271-419f-ba68-7b21cb794084 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
billy@billy-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
billy@billy-desktop:~$ 
----------------------------------
i have no idea what to make of it.

---

### Post by computer wizard on 2009-01-25
if it helps i need to access
Disk /dev/sdb: 40.0 GB, 40020664320 bytes
and i want it to mount at boot
please and thankyou

---

### Post by computer wizard on 2009-01-25
ok i have been thinking and could i be having problens because of a messed up MBR if so please help me with that, and i have already tries


-------

sudo apt-get install ms-sys

------
let me tell you it does not work! :(

i am trying to use a iso of the xp recovery counsol and i will be back lator this week because i am leaving to go to ------ and will be gone for a couple days any whys thankyou guys for the help and will talkto you lator. please e-mail me with any big ideas @ [email]wdorfner@hotmail.com[/email]

---

### Post by sisco311 on 2009-01-25
The partition table of the drive is messed up:
> Device Boot Start End Blocks Id System
/dev/sdb1 * 1 1 0 0 **Empty**
**Partition 1 does not end on cylinder boundary.**

I don't know how to help you with this, but I hope somebody with more experience can. Good luck.

---

### Post by blazemore on 2009-01-25
so what happens if you do
```
sudo mkdir /ntfs
```
```
sudo mount -t ntfs /dev/sdb1 /ntfs
```

---

