---
title: "help mounting a partition to automount"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-04-06
i had to do a re install of ubuntu 10.10 yesterday and did noticed that they change something. before if i had a partition that i didnt want to format. i could just skip and then make a mount point after i install. well you cant do that with the 10.10 cd. you keep getting error message. i was told that i have boot into a live cd and make a mount point. how would i do that i want to make a mount point for dev/sda3 ext4 i can name it anything.
output will follow in reply/tks

---

### Post by rburkartjo on 2011-04-06
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536   83  Linux
/dev/sda2           38209       38913     5662882    5  Extended
/dev/sda3            4080       34675   245762370   83  Linux
/dev/sda4           34676       38208    28378822+  83  Linux
/dev/sda5           38209       38913     5662881   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d6f0d6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121600   976751968+   7  HPFS/NTFS
ray@ray-GC660AA-ABA-SR5123WM:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=c46ad3d4-46d8-48ad-bed7-e3036efa5c3a /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=4dce963f-5a4a-4d91-9196-09b1d6ef8c76 none            swap    sw              0       0

---

### Post by ~Plue on 2011-04-06
> **rburkartjo said:**
> i had to do a re install of ubuntu 10.10 yesterday and did noticed that they change something. before if i had a partition that i didnt want to format. i could just skip and then make a mount point after i install. well you cant do that with the 10.10 cd. you keep getting error message.
are you sure that the 'use partition' box is unchecked? because usually,  only if its checked the installer would complain if a mount point isn't set....

---

### Post by rburkartjo on 2011-04-06
yes sure. that is a bug in the ubuntu 10.10 install or just a change in the setup so that from now on you have to specific a mount point for every partition during install

---

### Post by The Cog on 2011-04-06
Try making a mount point like this:
```
sudo mkdir /mnt/sda3
```
and then adding a line like this to /etc/fstab:
```
/dev/sda3  /mnt/sda3  ext4  defaults  0  2
```
Then mount it with this command:
```
sudo mount /dev/sda3
```

---

### Post by rburkartjo on 2011-04-06
cog thanks will give that a try with a live cd. will label this thread as solved if works

---

### Post by Paqman on 2011-04-06
> **rburkartjo said:**
> cog thanks will give that a try with a live cd. 

You should do this when logged into your normal install, not a LiveCD.

---

### Post by rburkartjo on 2011-04-07
tks paq wasnt sure that is why i waited. will do as you say

---

### Post by vanadium on 2011-04-07
You also should use UUID instead of device name (e.g. /dev/sda3). Using a device name is not always guaranteed to work consistently (although in your case, it might).

Learn the UUID of the partition you want to mount from the command "sudo blkid". Replace the reverence by device name by a reference by UUID. See the other lines in your /etc/fstab for examples.

---

### Post by 1991sudarshan on 2011-04-07
Try using Mount manager for auto mounting!

**sudo apt-get install mountmanager**

---

### Post by rburkartjo on 2011-04-07
tks ya'll got it to work

---

