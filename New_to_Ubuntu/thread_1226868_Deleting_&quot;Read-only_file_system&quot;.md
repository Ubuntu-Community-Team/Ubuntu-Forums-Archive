---
title: "Deleting &quot;Read-only file system&quot;"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by ozzyprv on 2009-07-30
How do I get around the "Read-only file system"?
I need to delete the whole folder.

```
me@mybox:/media/USB01/box02/home$ sudo rm -rf .mozilla/
rm: cannot remove `.mozilla/firefox/profiles.ini': Read-only file system
rm: cannot remove directory `.mozilla/firefox/dv52d9vq.default': Read-only file system 

```

Thank you.

---

### Post by Malta paul on 2009-07-30
Alt F2, Gksudo nautilus (caution you will now been in permanent root) right click your file, go to properties and change to 'read and write' then send it to trash bin.

:D

---

### Post by ozzyprv on 2009-07-30
> **Malta paul said:**
> Alt F2, Gksudo nautilus (caution you will now been in permanent root) right click your file, go to properties and change to 'read and write' then send it to trash bin.

:D

I am running that machine headless...no gnome....
Any other alternative?

---

### Post by ozzyprv on 2009-08-03
*bump*

---

### Post by koleoptero on 2009-08-03
<snip>

Didn't read the OP correctly, sorry.

---

### Post by braete on 2009-08-03
usb? card? pendrive?

---

### Post by Volt9000 on 2009-08-03
Mount the disk and post the output of

```

cat /etc/mtab

```

This will show the list of currently mounted devices, and will (probably) indicate the device you're trying to delete from (USB stick?) is read-only.

How did you mount this file system to begin with?

---

### Post by wojox on 2009-08-03
Change the permissions. Logout and log back in.

---

### Post by ozzyprv on 2009-08-03
The files are within a folder. The folder is @ an external USB HD (500 GB). External HD is mounted as USB01 (below).

```
me@mybox:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda3 /home ext3 rw,relatime 0 0
/dev/sdb1 /media/Disk01 ext3 rw,relatime 0 0
/dev/sdc1 /media/Disk02 ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdd1 /media/USB01 vfat rw 0 0

```

---

### Post by Volt9000 on 2009-08-03
```

/dev/sdd1 /media/USB01 vfat rw 0 0

```

There's your hard drive, and it's already mounted as read-write.

I honestly don't know what to tel you-- try using rm -rf as other posters suggested.

---

### Post by kayvortex on 2009-08-03
What does,

```
ls -dlh /media/USB01/box02/home/.mozilla
```

output?

---

### Post by ozzyprv on 2009-08-03
> **kayvortex said:**
> What does,

```
ls -dlh /media/USB01/box02/home/.mozilla
```

output?

I get this:

```
drwxr-xr-x 3 root root 32K 2009-05-13 16:54
```

---

### Post by kayvortex on 2009-08-04
Well, "sudo rm -rf /media/USB01/box02/home/.mozilla" should work. Perhaps try recursively making everything writeable, just in case? Enter:

```
sudo chmod +w -R /media/USB01/box02/home/.mozilla
```

and then,

```
sudo rm -rf /media/USB01/box02/home/.mozilla
```

Be careful with these since you're acting with superuser privileges. (You could remount the disk so that the group ID is not set to root, but to plugdev, or something similar; and, in fact, I'd recommend this since it would be more secure. To do this, edit or add an entry in /etc/fstab with "gid=46" added to the list of mount options for /dev/sdd1).

---

