---
title: "root command"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-16
Hi,
i'm at the root of a live cd and i cant think of how to get to the root of my hdd. Can you remind me please?

---

### Post by rustutzman on 2010-07-16
```
sudo fdisk -l
```

I think from that you figure out which one is you hdd and then mount it.

Russ

---

### Post by emoguitarist06 on 2010-07-16
Live Cds are automatically root

So you should be able to click Places > HDD
choose the HDD it'll show the GB space
you're HDD in Places will show every partition if any

---

### Post by nnjond on 2010-07-16
Thanks for your help; I'm still going wrong somewhere? Can you see?

root@ubuntu:/# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea053

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60239   483864576   83  Linux
/dev/sda2           60239       60802     4519937    5  Extended
/dev/sda5           60239       60802     4519936   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16013852672 bytes
64 heads, 32 sectors/track, 15272 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a8f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15272    15638512    c  W95 FAT32 (LBA)
root@ubuntu:/# mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
root@ubuntu:/# cd /dev/
root@ubuntu:/dev# mount sda1
mount: can't find sda1 in /etc/fstab or /etc/mtab
root@ubuntu:/dev#

---

### Post by Zeike on 2010-07-16
the proper syntax for mount is

'mount blockdevice destination'

So you probably want something like

```
mount /dev/sda1 /mnt
cd /mnt
```

---

### Post by garvinrick4 on 2010-07-16
If you want to get into root it is easier to label your install in gparted or disk utility.
If you labeled it lucid for example this would be your code.

```
sudo mkdir /media/lucid
```
```
sudo mount /dev/sda1 /media/lucid
```
```
sudo cp /etc/resolv.conf /media/lucid/etc/resolv.conf
```
```
sudo chroot /media/lucid
```
Now you have internet connection and are in root.

Made a label
Made a directory
Mounted your install
Copied internet connection to install
Put yourself in as root.
Remember you do not use sudo now.

From now on that install is always mounted at /media/lucid unless you change it.

---

