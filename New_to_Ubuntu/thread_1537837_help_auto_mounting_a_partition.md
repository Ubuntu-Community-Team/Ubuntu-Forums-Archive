---
title: "help auto mounting a partition"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-24
okay first i ran this command to backup just in case
sudo cp /etc/fstab /etc/fstab-old
because last time i  could not get it to work 

here is the outputs you need


ray@ray-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda4       /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=4dce963f-5a4a-4d91-9196-09b1d6ef8c76 none            swap    sw              0       0
ray@ray-desktop:~$ sudo fdisk -l
[sudo] password for ray: 

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
ray@ray-desktop:~$ sudo blkid
/dev/sda1: UUID="4ebbd675-075f-4fb0-91a1-a3b20e7721bc" TYPE="ext4" 
/dev/sda3: UUID="93bb2ea0-db9a-42a4-aa06-f47c4d9cb20c" TYPE="ext4" 
/dev/sda4: UUID="c46ad3d4-46d8-48ad-bed7-e3036efa5c3a" TYPE="ext4" 
/dev/sda5: UUID="4dce963f-5a4a-4d91-9196-09b1d6ef8c76" TYPE="swap" 


okay i want to automount the second /dev/sd3

how do i proceed and tks in advance

---

### Post by mikewhatever on 2010-07-24
Create the mount point, let's say, /media/data (obviously you can chose a different one):
```
sudo mkdir /media/data
```
Add the following line to fstab:
```
/dev/sda3 /media/data ext4 defaults 0 2
```

---

### Post by rburkartjo on 2010-07-24
mike tks for the help worked great. i noticed that there was another thread about auto mounting but wanted to make sure i did it right for my system.

---

### Post by Morbius1 on 2010-07-24
```
/dev/sda3 /media/data ext4 defaults 0 3
```I think there's a typo in there. The last digit, "3" in this case" determines the relative order of when a filesystem check is done at boot. I'm almost certain the possible values are 0 ( which turns it off ), 1 ( for the root partition ) , and 2. I don't think there is a "3".

---

### Post by rburkartjo on 2010-07-24
mor i thought that might be true also that is why i backup fstab first but what mike gave me worked

---

### Post by mikewhatever on 2010-07-24
> **Morbius1 said:**
> ```
/dev/sda3 /media/data ext4 defaults 0 3
```I think there's a typo in there. The last digit, "3" in this case" determines the relative order of when a filesystem check is done at boot. I'm almost certain the possible values are 0 ( which turns it off ), 1 ( for the root partition ) , and 2. I don't think there is a "3".

Indeed, thanks for pointing that out. I'll edit the post above.
```
    
    * 0 == do not check.
    * 1 == check this partition first.
    * 2 == check this partition(s) next 

```
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by rburkartjo on 2010-07-24
mike why did it work then i did it has you original posted and seems to work fine? if so what should i change it to/tks

---

### Post by rburkartjo on 2010-07-24
should the last read 0 and not 3 easy enough to change

---

### Post by Morbius1 on 2010-07-24
I would vote for "2". Since it's a data partition I would like it to check every now and then.

---

### Post by mikewhatever on 2010-07-24
> **rburkartjo said:**
> mike why did it work then i did it has you original posted and seems to work fine? if so what should i change it to/tks

Apparently, that number doesn't prevent the partition from being mounted. If you want it checked occasionally, go for '2', if not, then '0'.

---

### Post by rburkartjo on 2010-07-24
tks mor and mike took your advise and changed to 2

---

