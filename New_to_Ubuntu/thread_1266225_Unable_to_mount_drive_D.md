---
title: "Unable to mount drive D:/"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by senshisheena on 2009-09-14
Hi,

When I decided to try Ubunto, i saved my files in D:/ reformatted my C:// and install my Ubuntu in C://

Then when i tried to access my D://, i got this error:
"You are not privileged to mount this volume <vname>"

Well, i tried some steps i read in the forums like:
 
bombarda@bombarda:~$ sudo fdisk -l
[sudo] password for bombarda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f4c2f4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+  83  Linux
/dev/sda2            4865        9728    39070080    f  W95 Ext'd (LBA)
/dev/sda5            4865        9728    39070048+   7  HPFS/NTFS
bombarda@bombarda:~$ sudo umount /dev/sda2 /media/disk
umount: /dev/sda2: not mounted
umount: /media/disk: not mounted
bombarda@bombarda:~$ sudo mount /dev/sda2 /media/disk
mount: you must specify the filesystem type

- i don't know how to continue. It's my first time to use Ubuntu. I appreciate any help given.

Many thanks!
Sheena

---

### Post by Bachstelze on 2009-09-14
As the error says, you must specify the filesystem your partition is formatted in. This is done with the -t option of mount, so if your partition is NTFS:

```
sudo mount -t ntfs /dev/sda2 /media/disk
```

will do the trick.

---

### Post by NoaHall on 2009-09-14
Are you sure it's that one you want to mount? /dev/sda5 looks like the one you might want.

However, try "sudo mount /dev/sda2 /media/disk -t fat32"

Or, if it's the NFTS one you want, run "sudo apt-get install ntfs-3g" then you'll be able to do it via Places -

---

### Post by oldfred on 2009-09-14
If you are manually mounting your have to make the mount point first.

mkdir mount-point

then:
mount -t ntfs-3g /dev/sda5 /path_to/mount_point

If you want to see what is mounted 

sudo blkid -L

It looks like sda2 is just the extended partition which is a container for additional partitions. you need to mount sda5

---

