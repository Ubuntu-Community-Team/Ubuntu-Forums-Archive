---
title: "how to find the fstype"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by john77eipe on 2010-12-06
Hi,

I read that it's possible to mount devices by using the File system type. Also read that available partitions are present in /etc/fstab and already mounted partitions are in /etc/mtab.
But in fstab I found entry for sda7(ext4 my ubuntu partition) and sda6(swap).

The disk utility software shows that there are sda1, sda2, sda3 and sda5. All NTFS. How do I mount them using the cmd line?

```

/$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

```

---

### Post by ddnev45 on 2010-12-06
You need to specify where to mount sda1 etc ... For example:

```
sudo mount /dev/sda1 /mnt/windows
```

the /mnt/windows is a directory (mount point) you create - it can be /home/<YourUserName>/windwos etc ...

If you get an error requiring the filesystem type, use the "-t" switch to specify the type.

```
sudo mount -t ntfs-3g /dev/sda1 /mnt/windows
```

If you want to automount the ntfs partitions at boot up there are some tutorials in the Tutorials and Tips section of the forum. I think this information is still valid - [HowTo mount NTFS.]("http://ubuntuforums.org/showthread.php?t=785263&highlight=mount+ntfs")

---

### Post by karthick87 on 2010-12-06
To find the filesystem type,
```
sudo parted -l
```

---

### Post by matt_symes on 2010-12-06
Hi

....or (in a terminal type command press enter and then enter your password)

sudo fdisk -l

(that is  small L) will also tell you the  file system type. As will..

sudo blkid

This will also give you the UUID's you can use in fstab

Kind regards

---

### Post by john77eipe on 2010-12-07
thanks a ton guys! sorry i couldn't for the late response. :redface:

---

