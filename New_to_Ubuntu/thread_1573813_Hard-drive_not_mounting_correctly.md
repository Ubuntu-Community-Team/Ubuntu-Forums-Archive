---
title: "Hard-drive not mounting correctly"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2010-09-13
Hi,

My External USB hard drive is not mounting in the correct directory and is switching places with the backup drive.


When I browse to the hard-drive through Nautilus it appears correctly mounted. When I browse to the hard drive with the terminal, it has switched positions with the backup drive.

Can someone tell me how to solve this please?

```
sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72228f44

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          33      265041   83  Linux
/dev/sda2           18057       24321    50323612+   5  Extended
/dev/sda4              34       18056   144769747+  83  Linux
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris
/dev/sda6           18057       21823    30258364+  83  Linux
/dev/sda7           21824       24133    18555043+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000145a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dccf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

## THIS IS THE EXTERNAL USB DRIVE. IT IS 1TB (in theory)
Disk /dev/sdd: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002ae3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121515   976069206   83  Linux
```

---

### Post by Mega_Fauna on 2010-09-13
Solved. Mounted using UUIDs.

**Lesson 01:** Always and ever mount external USB and such hard-drives with UUIDs. If they are external, they will be unplugged and moved, and then Linux changes the mount points when remounted unless you use the *Universally Unique Identifier* method. This is disastrous if the hard-drives mirror each other as the sources and mirrors may be unknowingly flipped.

**Lesson 02:** Have root own backup drives so you can't accidentally work on them rather than the main drive.

**Lesson 03:** Use CLI not *Nautilus* which confuses hard drive with their mounting points and tells you they're mounted correctly.

```
UUID=b0494ef6-73ed-4282-940a-10e96af634c5 /media/MIRROR_02_OF_02  ext3         defaults                                                                   0  0  
UUID=02b80c63-93c7-4081-8284-d9faffe1d0c4 /media/MIRROR_01_OF_02  ext3         defaults                                                                   0  0   
UUID=8e47b60e-a6b9-4d69-b790-df17d3aaf23b /media/ST_JEROME        ext3         defaults                                                                   0  0  
```

---

### Post by gordintoronto on 2010-09-13
> **Mega_Fauna said:**
> Solved. Mounted using UUIDs.
[/CODE]

How does one do that, please?

---

### Post by Mega_Fauna on 2010-09-14
Hi gordintoronto,

Here are the steps I followed. *UUIDs* allow the hard drives to be unplugged and replugged in without having them loosing their correct mounting points (newb explanation). So if your drives are moving around, use *UUIDs*.

**1. Check we're working with the correct hard-drive.**

```
sudo fdisk -l
```

Lists all your hard drives and partitions. Here is the output describing my Terabyte drive. We really don't need this but it acts as a sort of double check to make sure that my /sdc1 drive is the correct size (1 TB) as if it weren't I'd be working with the wrong drive. *fdisk* is a safety check.

```
Disk /dev/sdc: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002ae3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121515   976069206   83  Linux
```


**2. Get the Universally Unique Identifier** for the hard drive.

```
sudo blkid
```

Below is output for ST_JEROME.

```
/dev/sdc1: LABEL="ST_JEROME" UUID="8e47b60e-a6b9-4d69-b790-df17d3aaf23b" TYPE="ext3"
```


**3. Fstab. **Make a backup of fstab. Then open fstab and paste the new code in over the old mounting method.

```
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab
```

Replace the line:

```
/dev/sdc1    /media/ST_JEROME        ext3         defaults                                                                   0  0
```

with the UUID line:

```
UUID=8e47b60e-a6b9-4d69-b790-df17d3aaf23b /media/ST_JEROME        ext3         defaults                                                                   0  0
```

For information on understanding fstab start [_here_]("https://help.ubuntu.com/community/Fstab"). An explanation of UUIDs is [_here_]("https://help.ubuntu.com/community/UsingUUID"). The second page includes alternative methods of identifying drives and upgrading fstab. I personally recommend the Ubuntu community pages to learn the basics from, they are a beginners starting point, followed by Google and the manual command.

For the record, St. Jerome is the patron saint of librarians, this is my first terabyte drive:)

---

### Post by gordintoronto on 2010-09-14
Thanks!

---

