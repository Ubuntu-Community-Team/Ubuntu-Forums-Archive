---
title: "What is wrong with this init script?"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by Fanatico on 2011-04-10
I need to write my own custom init script for creation initrd image. Unfortunately Linux booting fails to create root file system on sda3.

The script fails at line
mount -o defaults --ro -t ext4 /dev/sda3 /sysroot

Can anyone advise what is wrong in the script?

My partition configuration is as follows:
sda1 - windows
sda2 - linux boot
sda3 - linux root
sda4 - linux swap

Init script:

#!/bin/nash

mount -t proc /proc /proc
#setquiet
echo Mounting proc filesystem
echo Mounting sysfs filesystem
mount -t sysfs /sys /sys
echo Creating /dev
mount -o mode=0755 -t tmpfs /dev /dev
mkdir /dev/pts
mount -t devpts -o gid=5,mode=620 /dev/pts /dev/pts
mkdir /dev/shm
mkdir /dev/mapper
mknod /dev/sda b 3 0
mknod /dev/sda1 b 3 1
mknod /dev/sda2 b 3 2
mknod /dev/sda3 b 3 3
mknod /dev/sda4 b 3 4

...

mkblkdevs
echo waiting for root device to appear (timeout 1min)
waitdev --timeout=15000000 --rootdev=/dev/sda3
echo Resume swap partition
resume /dev/sda4
echo Creating root device.
mkrootdev -t ext4 -o relatime,defaults,data=writeback,ro /dev/sda3
echo Mounting root filesystem.
mount -o defaults --ro -t ext4 /dev/sda3 /sysroot
echo Setting up other filesystems.
setuproot
loadpolicy
plymouth --newroot=/sysroot
echo Switching to new root and running init.
nash-if-splash splashy_update "chroot /sysroot"
switchroot
echo Booting has failed.
nash-if-splash splashy_update exit
nash-if-splash splashy_chvt 1
sleep -1
init

---

