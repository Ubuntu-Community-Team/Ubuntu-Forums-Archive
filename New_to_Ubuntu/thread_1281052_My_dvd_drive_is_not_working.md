---
title: "My dvd drive is not working"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by Vichfret on 2009-10-02
My dvd driver is not reading any DVDs, I tried with different dvds and different brands but it just doesn't mount the disc, what can I do?

---

### Post by halitech on 2009-10-02
does the light come on and can you hear it spin up? Are you trying to get a blank dvd to mount so you can burn it or read what has already been burned?

---

### Post by Vichfret on 2009-10-02
yes, the light is on and I can hear it is reading it but it looks like it isn't mounting, it's already burned.

---

### Post by halitech on 2009-10-02
ok, those are good signs. Try opening a terminal and running these commands and posting the output
```
mount
```and
```
sudo fdisk -l
```

---

### Post by Vichfret on 2009-10-02
```
19:52:50 maggie:~ > mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /media/windows type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/storage type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
19:52:51 maggie:~ > su
Password: 
Fri Oct  2 19:52:56 CDT 2009

19:52:56 maggie:/home/vicfred # fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7649    61440088+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7649       26771   153596520    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           26772       30515    30073680   83  Linux

```

---

### Post by halitech on 2009-10-02
not showing there...

okay, post the results of
```
cat /etc/fstab
```

---

### Post by Vichfret on 2009-10-02
```
19:52:58 maggie:/home/vicfred # cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=e7ef7189-55b8-4c2e-83b8-6fee593ff8a7 /               ext4    errors=remount-ro 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/windows    ntfs-3g        rw,auto,user,fmask=0111,dmask=0000,nls=utf8    0    0
/dev/sda2       /media/storage    ntfs-3g        rw,auto,user,fmask=0111,dmask=0000,nls=utf8    0    0

```

---

### Post by credobyte on 2009-10-02
```
sudo mount /dev/hdb /media/cdrom0

```

What's the output ?

---

### Post by kansasnoob on 2009-10-02
What version of Ubuntu are you running?

The output of:

```
cat /etc/issue
```

would be helpful.

---

### Post by Vichfret on 2009-10-02
```
mount: block device /dev/hdb is write-protected, mounting read-only
mount: you must specify the filesystem type

```But it worked with:
```
20:02:36 maggie:/home/vicfred # mount -t iso9660 /dev/hdb /media/cdrom0
```

@[COLOR=Black]kansasnoob

I use Debian squeeze.[/COLOR] []("http://ubuntuforums.org/member.php?u=554595")

---

