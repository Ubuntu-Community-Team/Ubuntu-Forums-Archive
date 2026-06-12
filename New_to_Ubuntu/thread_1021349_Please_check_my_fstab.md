---
title: "Please check my fstab"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-12-25
I want my partitions sd5, 6, 7, 8, 10 to be read & write. but they are ready only.

Here is my fstab

> proc            /proc           proc    defaults        0       0
/dev/sda1 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda9 /home           ext3    relatime        0       1
/dev/sda10 /media/disk1   ext3    user,rw,auto    0       0
/dev/sda5 /media/disk2    vfat    defaults         0       0
/dev/sda6 /media/disk3    vfat    defaults        0       0
/dev/sda7 /media/disk4    vfat    defaults        0       0
/dev/sda8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


here are /media details

> manu@ubuntu:~$ ls -al /media
total 28
drwxr-xr-x  7 root root 4096 2008-12-26 02:26 .
drwxr-xr-x 20 root root 4096 2008-12-25 21:27 ..
lrwxrwxrwx  1 root root    6 2008-12-25 21:25 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-12-25 21:25 cdrom0
drwxrwxrwx  2 manu manu 4096 2008-12-25 21:25 disk1
drwxrwxrwx  2 manu manu 4096 2008-12-26 01:05 disk2
drwxrwxrwx  2 manu manu 4096 2008-12-26 01:06 disk3
drwxrwxrwx  2 manu manu 4096 2008-12-26 01:07 disk4
-rw-r--r--  1 root root    0 2008-12-26 02:26 .hal-mtab

---

### Post by taurus on 2008-12-25
/dev/sda8 is swap partition so forget about writing to it.  It's out.

If you want to write to /media/disk1 (/dev/sda10), you need to change the ownership of /media/disk1 from root to your username.

```
sudo chown -R manu:manu /media/disk1
```

And for the other three vfat partitions, you can edit /etc/fstab and make them look something like these.

```

/dev/sda5 /media/disk2 vfat iocharset=utf8,umask=000 0 0
/dev/sda6 /media/disk3 vfat iocharset=utf8,umask=000 0 0
/dev/sda7 /media/disk4 vfat iocharset=utf8,umask=000 0 0

```
Then reboot.

---

### Post by Guruprasad on 2008-12-25
sda5,6,7 started working as r&w.

sda10 still works readonly...

---

### Post by taurus on 2008-12-25
I would edit /etc/fstab and change the entry for /dev/sda10 to this.

```
/dev/sda10 /media/disk1 ext3 defaults 0 2
```
Reboot.  

Then, change the ownership of /media/disk1 from root to your username again.

```
sudo chown -R manu:manu /media/disk1
```

---

### Post by Guruprasad on 2008-12-25
yup solved.. thanks alot..

---

