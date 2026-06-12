---
title: "My fstab configuration does not works. So it does not mount any partition"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by legolas_w on 2008-12-06
Hi
Thank you for reading my post.
I have Ubuntu 8.10 and I add following lines to /etc/fstab file to make sure my partition mounts on boot.
but none of them mount when Ubuntu loads.

```

/dev/sda5 /media/dep ntfs-fuse auto,gid=1000,umask=0002 0 0
/dev/sda1 /media/Sys ntfs-fuse auto,gid=1000,umask=0002 0 0
/dev/sdb5 /media/lib ntfs-fuse auto,gid=1000,umask=0002 0 0
/dev/sdb1 /media/Torrent ntfs-fuse auto,gid=1000,umask=0002 0 0
/dev/sda2 /media/Old ntfs-fuse auto,gid=1000,umask=0002 0 0

```

My gid is 1000, I found it using System=>Administration=>Users & Groups command.

I should say that I create all of those folder inside the /media folder using a nautilus executed by "gksudo nautilus" command. I did not gives "legolas" which is my username any permission on those folders because I have not seen any text which indicate it is required.

Would you please let me know what is wrong?

Thanks.

---

### Post by cdtech on 2008-12-06
Could we see the output of the command:
```
sudo fdisk -l
```

---

### Post by legolas_w on 2008-12-06
Hi, Thank you and here is the output for sudo fdisk -l


```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c212

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2           12749       19122    51199155    7  HPFS/NTFS
/dev/sda3           19123       38487   155549362+   f  W95 Ext'd (LBA)
/dev/sda4            6375       12748    51199155   83  Linux
/dev/sda5           19123       38244   153597433+   7  HPFS/NTFS
/dev/sda6           38245       38487     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08e408e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       15298    61440592+   f  W95 Ext'd (LBA)
/dev/sdb3           15299       24321    72477247+  83  Linux
/dev/sdb5            7650       15043    59392273+   7  HPFS/NTFS


```

---

### Post by kpkeerthi on 2008-12-06
Why ntfs-fuse? Change it to ntfs-3g and type
```
sudo mount -a
```
This should mount the partitions defined in FSTAB. Post back the errors if any.

---

### Post by vanadium on 2008-12-06
I am not sure the file system type ntfs-fuse is valid. Where did you find that?

Change ntfs-fuse to ntfs-3g. All else looks all right as far as I can tell.

After the changes, you can check wether all is OK by using the command

```

sudo mount -a

```
This will execute all mounts in /etc/fstab and normally produces no output at all. There is only output if there are errors. If that is the case, post te output here so people can help you with further troubleshooting.

---

### Post by kpkeerthi on 2008-12-06
The mount options for NTFS should look like
```

/dev/hda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

```

See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for details on NTFS

---

### Post by cdtech on 2008-12-06
The fuse is old just use ntfs. No need for the ntfs-3g that's been updated with the new kernel.

You could also try the command line and see if it mounts.
```
sudo mount -t ntfs /dev/sda5 /path_to/mount_point
```

---

### Post by pwicken on 2008-12-08
I do think the fstab in 8.10 demands the UUID of the partition.
```
sudo vol_id -u /dev/sda6
```
and the line in fstab should look like

#/dev/sda6
UUID=c0bec7d9-7218-47c7-8d1d-81790c30f1a6   /home        ext3     defaults,errors=remount-ro 0 1

where the mount is commented away and replaced with the actual UUID.

---

### Post by kpkeerthi on 2008-12-10
> **pwicken said:**
> I do think the fstab in 8.10 demands the UUID of the partition.

Well... it does not demand but it is advisable to use UUID as against device names due to the (recent) changes in the way udev names devices. It is quite possible that udev identifies and names your device differently each time.

---

### Post by MeURi on 2008-12-10
Also, a more tweaked fstab entry for NTFS partitions could be
```

UUID=<your partition's UUID> /media/<mountpoint> ntfs-3g users,uid=1000,gid=46,fmask=0113,dmask=0002,locale=en_US.utf8 0 1 

```

Found it somewhere, and don't remember each option in detail, but the dmask and fmask masks prevent the "Windows" files from being always executable, which I find rather annoying.

EDIT: ok, found the reference for that entry; I found it [here](http://wiki.archlinux.org/index.php/NTFS_Write_Support) while playing with Arch, some time ago.

---

