---
title: "ide drives do not register"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by sinbosun on 2009-01-10
I have just installed ubuntu 8.10 on a 1terabyte sata dual boot win xp and ubuntu. I have two older drives (IDE). They do not register at all on the places menu or on my computer. I tried sudo fdist -l
and recieved as follows:
john@john-desktop:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedafedaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       95101   763898751    7  HPFS/NTFS
/dev/sda2           95102      121601   212861250    5  Extended
/dev/sda5           95389      120845   204483321   83  Linux
/dev/sda6          120846      121601     6072538+  82  Linux swap / Solaris
/dev/sda7           95102       95367     2136582   83  Linux
/dev/sda8           95368       95388      168651   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f982f97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7473    60026841    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf70bce2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcea0509f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       60801   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdf: 32 MB, 32243712 bytes
4 heads, 32 sectors/track, 492 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x009a4d52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         491       31408    4  FAT16 <32M

Disk /dev/sdh: 1030 MB, 1030225920 bytes
32 heads, 63 sectors/track, 998 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x0003255a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1         998     1005952+   6  FAT16

Disk /dev/sdj: 1039 MB, 1039663104 bytes
32 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1   ?      392206      967564   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(392205, 19, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(967563, 8, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdj2   ?       85025     1060846   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(85024, 30, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1060845, 20, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdj3   ?      942481     1918302   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(942480, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1918301, 7, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdj4   ?           1     1833280  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1833279, 15, 30)
Partition 4 does not end on cylinder boundary.

How can I mount these?

---

### Post by nhasian on 2009-01-10
good news is that fdisk can see them.  in addition to your 1TB hard disk, i also see /dev/sdb: 122.9 GB, /dev/sdc: 200.0 GB, /dev/sde: 500.1 GB

you can add these devices to the /etc/fstab so they are mounted automatically on startup but we will need the UUIDs to do it right. please give us the out put of:

```
ls /dev/disk/by-uuid -lah
```

here's more info on fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by ajgreeny on 2009-01-10
Do you really need them all mounted every time you boot?  If you don't, have a look at the **Disk Mounter** panel applet which allows you to mount them easily with small panel icons.  It's how I do it always now.

---

### Post by sinbosun on 2009-01-10
> **nhasian said:**
> good news is that fdisk can see them.  in addition to your 1TB hard disk, i also see /dev/sdb: 122.9 GB, /dev/sdc: 200.0 GB, /dev/sde: 500.1 GB

you can add these devices to the /etc/fstab so they are mounted automatically on startup but we will need the UUIDs to do it right. please give us the out put of:

```
ls /dev/disk/by-uuid -lah
```

here's more info on fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
john@john-desktop:~$ ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 260 2009-01-10 10:55 .
drwxr-xr-x 6 root root 120 2009-01-10 03:55 ..
lrwxrwxrwx 1 root root  10 2009-01-10 10:55 10D8-132E -> ../../sde1
lrwxrwxrwx 1 root root  10 2009-01-10 03:55 20F08CD2F08CAF98 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-01-10 10:55 3A83-BC31 -> ../../sdh1
lrwxrwxrwx 1 root root  10 2009-01-10 03:55 9b1a6f3a-3f15-4746-a239-173c4dead32d -> ../../sda6
lrwxrwxrwx 1 root root  10 2009-01-10 03:55 a1b6a80c-ac2c-4315-a485-626c09764936 -> ../../sda5
lrwxrwxrwx 1 root root  10 2009-01-10 03:55 abcde25f-b39f-4a8b-9e34-0e853fc7df6d -> ../../sda7
lrwxrwxrwx 1 root root   9 2009-01-10 10:55 ACAD-2E23 -> ../../sdj
lrwxrwxrwx 1 root root  10 2009-01-10 03:55 bbdb8f74-40bb-49a7-a151-12b0a61ebfb1 -> ../../sda8
lrwxrwxrwx 1 root root  10 2009-01-10 03:55 C258481958480F1B -> ../../sdc1
lrwxrwxrwx 1 root root  10 2009-01-10 10:55 D2AF-C2D9 -> ../../sdf1
lrwxrwxrwx 1 root root  10 2009-01-10 03:55 E8A0D21CA0D1F154 -> ../../sdb1
john@john-desktop:~$ 
I have a 500 gig usb drive which is seen and a couple of flash drives. I need the two ide drives with all my data on them.

---

### Post by nhasian on 2009-01-10
okay first lets make the mountpoint.  I'll call it 500G or you can substitute whatever name you'd like.

```
sudo mkdir /media/500G
```

now lets make a backup copy of your /etc/fstab incase it accidentally gets mucked up.

```
sudo cp etc/fstab /etc/fstab.backup
```

now lets edit it with gedit:

```
sudo gedit /etc/fstab
```

append to the end of the file and save:

```
# Disk /dev/sde: 500.1 GB
UUID=10D8-132E	/media/500G ntfs defaults,umask=007,gid=46 0 1
```

you can follow the steps to create more mountpoints but you need to use the correct UUID for whichever device you want to mount.

---

### Post by -kg- on 2009-01-10
> **nhasian said:**
> okay first lets make the mountpoint.  I'll call it 500G or you can substitute whatever name you'd like.

```
sudo mkdir /media/500G
```

now lets make a backup copy of your /etc/fstab incase it accidentally gets mucked up.

```
sudo cp etc/fstab /etc/fstab.backup
```

now lets edit it with gedit:

```
sudo gedit /etc/fstab
```

append to the end of the file and save:

```
# Disk /dev/sde: 500.1 GB
UUID=10D8-132E	/media/500G ntfs defaults,umask=007,gid=46 0 1
```

you can follow the steps to create more mountpoints but you need to use the correct UUID for whichever device you want to mount.

Does sinbosun require the ability to write to the partition as well as reading it?  If so, the line should read:

```
# Disk /dev/sde: 500.1 GB
UUID=10D8-132E	/media/500G ntfs**[COLOR="Red"]-3g[/COLOR]** defaults,umask=007,gid=46 0 1
```

(The addition in red)

Of course, you will need to go into Synaptics and ensure that you have ntfs-3g installed.

---

### Post by nhasian on 2009-01-12
I can read/write to my partition just fine without the 3G.  i think thats a different driver altogether that is not installed by default in ubuntu.

> **-kg- said:**
> Of course, you will need to go into Synaptics and ensure that you have ntfs-3g installed.

---

### Post by -kg- on 2009-01-12
> **nhasian said:**
> I can read/write to my partition just fine without the 3G.  i think thats a different driver altogether that is not installed by default in ubuntu.

Maybe you're using a different distro.  I'm using 8.04, and I went through this issue and had to install the ntfs-3g driver and note it as such in my fstab for auto-mounting so that I could write to the drive as well as reading it.

I was instructed to use this in [http://ubuntuforums.org/showthread.php?t=1013141]("http://ubuntuforums.org/showthread.php?t=1013141").  Scroll down to the second from the bottom post by bodhi.zazen in which he instructed me to use that entry in my fstab for rw support for an ntfs partition.

Also read bodhi.zazen's Tutorial, [How To Fstab.]("http://ubuntuforums.org/showthread.php?t=283131&highlight=How+To+Fstab")

---

