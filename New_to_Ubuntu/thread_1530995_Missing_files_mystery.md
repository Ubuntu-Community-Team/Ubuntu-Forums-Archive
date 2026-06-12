---
title: "Missing files mystery"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-14
Hi,

I wonder if anyone can advance my understanding of this problem; perhaps to a remedy or conclusion?


My intention was to copy some files from the home dir to an external 250 Gb hdd via usb. I attempted to format and partition the target sdb several times but Gpart kept failing. Then i right clicked on the sdb desktop icon and saw other options to format:

I recall choosing ex 4, in any case not a FAT.


I used a live 10.04 to copy across files from home dir, to hdd b. with sudo privilege, and they seem to have arrived, as i'm sure i checked.

Now, after a fresh install of 10.04, when i try to transfer them back to the home dir, the desktop icon doesn't show up. -and  Gpart identifies sdb as "Unallocated". Can you be certain there are no files on this hdd?

I'm sorry but i'm not very able to interpret the results from the 1st steps in the inquiry.


nnjond@nnjond-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3c30ba43-6de6-4e68-856b-e5495254bbfa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2c3e1b82-4ea9-4e53-82ab-718d9d6e465f none            swap    sw              0       0
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ sudo fdisk -l
[sudo] password for nnjond: 

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

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e67e

   Device Boot      Start         End      Blocks   Id  System
nnjond@nnjond-desktop:~$ 


I also  attempted to follow this advice, not understanding where it led me:


“Try mounting the drive as follows:”

Code:
cd /mnt
sudo mkdir ext_drive
sudo mount /dev/sdb ext_drive
cd ext_drive
ls


nnjond@nnjond-desktop:~$ cd /mnt
nnjond@nnjond-desktop:/mnt$ sudo mkdir ext_drive
mkdir: cannot create directory `ext_drive': File exists
nnjond@nnjond-desktop:/mnt$ sudo mount /dev/sdc ext_drive
mount: you must specify the filesystem type
nnjond@nnjond-desktop:/mnt$ 


Thanks for your time

---

### Post by cariboo on 2010-07-14
Your error message tells you what to do. you need to use the -t option. If your device is formatted as ext4 the command would be:

```
sudo mount -t ext4 /dev/sdc1 /mnt/ext_drive 
```

---

