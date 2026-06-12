---
title: "auto maount two drives"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by DarinB on 2009-04-04
help auto mounting the two extra drives one for a home folder and the other for music
darin@darin-desktop:~$ sudo fdisk -l
[sudo] password for darin: 

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11446ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48092   386296828    7  HPFS/NTFS
/dev/sda2           48093       91201   346273042+   5  Extended
/dev/sda5           48093       90066   337156123+  83  Linux
/dev/sda6           90067       91201     9116856   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x790b9718

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x790b971b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdi'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdi: 4095 MB, 4095606784 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1         497     3992135+   b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 254, 63) logical=(0, 0, 35)
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(496, 254, 63)
darin@darin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e2ec7b35-1e1c-4d1c-8d45-ca3df398d48e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=751c0a41-95f0-41b0-ab41-8964640b0a2c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
darin@darin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             317G  2.9G  298G   1% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  100K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  616K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/scd0             8.0G  8.0G     0 100% /media/cdrom0
/dev/sdi1             3.8G  395M  3.5G  11% /media/disk
darin@darin-desktop:~$

---

### Post by kanikilu on 2009-04-04
It would probably help to know which devices you want to mount (and where you want to mount them). Also, putting that kind of stuff in [code] tags would help trying to read it...

By the way, if you don't already know how to edit fstab, you might want to look into the **pysdm** package.

---

### Post by DarinB on 2009-04-04
how do i use pysdm

---

### Post by DarinB on 2009-04-04
i think the old method will work better pysdm didn't work at all

---

### Post by Elfy on 2009-04-04
Still need to know which partitions you want help with though ;)

---

### Post by DarinB on 2009-04-04
that would be sdb and sdc i want one for my new home folder location and the other for music

---

### Post by DarinB on 2009-04-04
ok i want sdb to be the eventual location of my home folder
sdc to be my music folder
i need auto mount and boot and not visible on my desk top (i think mnt/music etc?)
here are the terminal results and i think i messed things up with pysdm (shouldn't touch what i don't know)
darin@darin-desktop:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11446ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48092   386296828    7  HPFS/NTFS
/dev/sda2           48093       91201   346273042+   5  Extended
/dev/sda5           48093       90066   337156123+  83  Linux
/dev/sda6           90067       91201     9116856   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x790b9718

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x790b971b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   83  Linux
darin@darin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda5
UUID=e2ec7b35-1e1c-4d1c-8d45-ca3df398d48e  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda6
UUID=751c0a41-95f0-41b0-ab41-8964640b0a2c  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdc1                                  /media/music sdc1  ext3         errors=remount-ro           0  0  
darin@darin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             317G  3.0G  298G   1% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  100K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  372K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
darin@darin-desktop:~$

---

### Post by DarinB on 2009-04-04
Ok i did this but it does not start at boot 
root@darin-desktop:/home/darin# sudo chown -R darin:darin /media/music
root@darin-desktop:/home/darin# ls -la /media
total 28
drwxr-xr-x  7 root  root  4096 2009-04-04 09:41 .
drwxr-xr-x 20 root  root  4096 2009-04-03 23:00 ..
lrwxrwxrwx  1 root  root     6 2009-04-03 22:36 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2009-04-03 22:36 cdrom0
-rw-r--r--  1 root  root     0 2009-04-04 09:41 .hal-mtab
-rw-------  1 root  root     0 2009-04-04 09:41 .hal-mtab-lock
drwxr-xr-x  3 darin darin 4096 2009-04-04 06:22 music
drwxr-xr-x  2 root  root  4096 2009-04-04 01:45 music sdc1
drwxr-xr-x  2 root  root  4096 2009-04-04 01:43 sdb1
drwxr-xr-x  2 root  root  4096 2009-04-04 01:46 sdc1
root@darin-desktop:/home/darin#

---

### Post by DarinB on 2009-04-04
ok now it works i have to figure out sdb1 to auto mount and then move my home folder there

---

### Post by accooper on 2009-04-04
There is an easier way.  Go to add/remove programs and look for the program named Disk Manager.

Install it and through the settings you can have it auto mount any drive or drive like object (ram drive external hard drive usb drives etc,).  I have found that this is a really helpful program.

:guitar:

Andrew

---

### Post by DarinB on 2009-04-04
I used disk manager but i have two problems i don't have user permissions now i have to change that not sure how to use chown

---

