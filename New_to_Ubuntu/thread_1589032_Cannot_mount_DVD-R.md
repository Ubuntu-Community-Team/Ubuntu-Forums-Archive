---
title: "Cannot mount DVD-R"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by llamaboy on 2010-10-05
I tried mounting a couple dvd-r's that I had burned. It comes up with the following

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and my /etc/fstab came up with the following:

-laptop:~$ /etc/fstab
bash: /etc/fstab: Permission denied

---

### Post by PapaNerd on 2010-10-05
And what did you get when you checked to messages?
```
 dmesg | tail 
```

You'll want to do
```
 cat /etc/fstab 
```
as just typing the file name would try to execute it.

---

### Post by llamaboy on 2010-10-05
-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d58c7db6-a196-4faf-908c-672a4360b395 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=636fe11e-34f3-4423-aadb-725d74be4c32 none            swap    sw              0       0






-laptop:~$ dmesg | tail
[11553.448026] ata1: SRST failed (errno=-16)
[11553.448036] ata1: soft resetting link
[11553.644053] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[11553.644060] ata1.00: revalidation failed (errno=-5)
[11553.644066] ata1.00: disabled
[11553.644112] ata1: soft resetting link
[11558.805044] ata1: link is slow to respond, please be patient (ready=0)
[11563.700039] ata1: SRST failed (errno=-16)
[11563.700051] ata1: soft resetting link
[11563.852725] ata1: EH complete

---

### Post by sandyd on 2010-10-05
> **llamaboy said:**
> I tried mounting a couple dvd-r's that I had burned. It comes up with the following

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and my /etc/fstab came up with the following:

-laptop:~$ /etc/fstab
bash: /etc/fstab: Permission denied

tried mounting as UDF?
```

sudo mkdir /media/cdrom
sudo mount -t udf /dev/sr0 /media/cdrom
```

---

### Post by llamaboy on 2010-10-05
-laptop:~$ sudo mkdir /media/cdrom
mkdir: cannot create directory `/media/cdrom': File exists

-laptop:~$ sudo mount -t udf /dev/sr0 /media/cdrom
mount: no medium found on /dev/sr0

---

