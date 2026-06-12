---
title: "[SOLVED] Fstab mounting issues"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by ukulele_ninja on 2008-12-17
By editing my fstab file I was able to get my two external hdd's to work with linux and all has been well for the past several days. Well, today something decided to be fickle and when I rebooted my drives are no longer mounting properly. They appear in my list by going to place>device name but when I click on them I get an error saying I dont have permission to mount the drive. How in the world could that be if they have worked flawlessly up to this point? Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6915cbe6-d092-41f5-9c9b-d9bc9430f8da /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=152e0c05-1385-4aed-b083-0a67f6a211ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=85484f0d-dcca-42d2-a0e8-e94881360639	/media/500GIG	XFS	defaults	0	2
UUID=cca87a16-6abb-423b-8b99-5440d1a6f2b5	/media/80GIG	XFS	defaults	0	2

---

### Post by wolfen69 on 2008-12-17
try in terminal: ```
sudo chown -R user:user /media/500GIG 
``` of course replacing user with your name.

---

### Post by wolfen69 on 2008-12-17
i forgot to add, reboot after.

---

### Post by ukulele_ninja on 2008-12-17
ryan@ryan-desktop:~$ sudo -R ryan:ryan /media/500GIG
sudo: illegal option `-R'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
ryan@ryan-desktop:~$

---

### Post by wolfen69 on 2008-12-17
post the output of ```
sudo fdisk -l
```

---

### Post by nandemonai on 2008-12-17
> **ukulele_ninja said:**
> ryan@ryan-desktop:~$ sudo -R ryan:ryan /media/500GIG
sudo: illegal option `-R'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
ryan@ryan-desktop:~$

Forgot the chown bit ;)

---

### Post by wolfen69 on 2008-12-17
> **nandemonai said:**
> Forgot the chown bit ;)

thanks for noticing that. it's getting real late here.

---

### Post by ukulele_ninja on 2008-12-17
> **wolfen69 said:**
> post the output of ```
sudo fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094765

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59667   479275146   83  Linux
/dev/sda2           59668       60801     9108855    5  Extended
/dev/sda5           59668       60801     9108823+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd49c832

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27dae78d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux
ryan@ryan-desktop:~$

---

### Post by taurus on 2008-12-17
Shouldn't "XFS" filesystem be lower case in /etc/fstab?

```
df -h
ls -la /media
```

---

### Post by ukulele_ninja on 2008-12-17
> **taurus said:**
> Shouldn't "XFS" filesystem be lower case in /etc/fstab?

```
df -h
ls -la /media
```

ryan@ryan-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             450G  4.4G  423G   2% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  100K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  496K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/scd0             4.0G  4.0G     0 100% /media/cdrom0
ryan@ryan-desktop:~$ ls -la /media
total 26
drwxr-xr-x  7 root       root       4096 2008-12-17 01:19 .
drwxr-xr-x 20 root       root       4096 2008-12-14 01:26 ..
drwxrwxrwx  2 ryan       ryan       4096 2008-12-14 11:31 500GIG
drwxrwxrwx  2 ryan       ryan       4096 2008-12-14 11:31 80GIG
lrwxrwxrwx  1 root       root          6 2008-12-14 00:39 cdrom -> cdrom0
dr-xr-xr-x  6 4294967295 4294967295 1164 2005-09-01 19:20 cdrom0
drwxr-xr-x  2 root       root       4096 2008-12-14 00:39 cdrom1
-rw-r--r--  1 root       root          0 2008-12-17 01:19 .hal-mtab
drwxr-xr-x  2 root       root       4096 2008-12-14 11:38 mount
ryan@ryan-desktop:~$ 

Theres the results of that. So change the file system to xfs in my fstab?

---

### Post by taurus on 2008-12-17
Yes.  Once you have made the changes, remount them with

```
sudo mount -a
df -h
```

---

### Post by ukulele_ninja on 2008-12-17
That was the issue! Thanks!

---

