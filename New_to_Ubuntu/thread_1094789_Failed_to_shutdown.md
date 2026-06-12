---
title: "Failed to shutdown"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by CarolinaGuy on 2009-03-13
My ubuntu 8.04 server failed to shutdown and I had to turn power off to regain control.

Now the server is not seeing either Drive B or Drive C
```
charlie@ubuntu8:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              54G  1.5G   50G   3% /
varrun                252M  188K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   52K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/sda3              19G  6.9G   11G  39% /mnt/Documents

```

I have run recovery mode but no luck.

My ftab seem to longer have drive C listed bit drive B is listed.
```
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=296e3c06-d850-440b-9c27-4c122aac4e3c /               ext3    relatime,erro$


# /dev/sda3
/dev/sda3       /mnt/Documents     ext3,   defaults, 0     0


# /dev/sda5
UUID=f43c0549-5d66-4fa5-afe1-99d20140b26f none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


# /dev/sdb1
/dev/sdb1       /mnt/photos     ext3,   defaults, 0     0
                               [ Read 26 lines ]


```

What is the proper way to handle this situation in the future; (failure to shutdown) and what do I need to do to get these two drives recognized again.

CarolinaGuy

---

### Post by taurus on 2009-03-13
Is that the complete /etc/fstab?  Why do you have a comma (,) after ext3 & defaults?


```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by CarolinaGuy on 2009-03-13
taurus,
THANKS for your help. The comma are just an error of a novice at ubuntu, namely ME.


```

charlie@ubuntu8:~$ sudo fdisk -l
[sudo] password for charlie:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040edd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7079    56862036   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda3            7080        9541    19776015   83  Linux
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order
charlie@ubuntu8:~$

```

```

charlie@ubuntu8:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=296e3c06-d850-440b-9c27-4c122aac4e3c /               ext3    relatime,errors=remount-ro 0       1


# /dev/sda3
/dev/sda3       /mnt/Documents     ext3,   defaults, 0     0


# /dev/sda5
UUID=f43c0549-5d66-4fa5-afe1-99d20140b26f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


# /dev/sdb1
/dev/sdb1       /mnt/photos     ext3,   defaults, 0     0


# /dev/sdb2
/dev/sdb2       /mnt/music     ext3,   defaults, 0     0

# /dev/sdc1
/dev/sdc1       /mnt/movies     ext3    defaults, 0     0

```

THANKS,
I'm in process of removing the commas after defaults.

CarolinaGuy

---

### Post by taurus on 2009-03-13
Looks like the other two external drives are not showing up at all, /dev/sdb1, /dev/sdb2, & /dev/sdc1.

I assume they are both plugged in and on.  What's the output of this command from a terminal.

```
dmesg | tail
```

---

### Post by CarolinaGuy on 2009-03-13
```

charlie@ubuntu8:~$ dmesg | tail
[   65.521971] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   73.859696] eth0: no IPv6 routers present
[   97.306796] EXT3 FS on sda1, internal journal
[   97.677131] kjournald starting.  Commit interval 5 seconds
[   97.677149] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   97.677368] EXT3 FS on sda3, internal journal
[   97.677376] EXT3-fs: mounted filesystem with ordered data mode.
[   98.574599] ip_tables: (C) 2000-2006 Netfilter Core Team
[  100.340763] ppdev: user-space parallel port driver
[  100.792870] audit(1236917523.694:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4586 profile="/usr/sbin/cupsd" namespace="default"
charlie@ubuntu8:~$

```

The BIOS auto detects B-DRIVE but it fails on boot 
The BIOS DOES NOT detects C-DRIVE and it fails on boot 

They are connected and everything was find until I went to shut the system down for the night. Have not been in the case.

CarolinaGuy

---

### Post by taurus on 2009-03-13
So looks like they both fail, according to the BIOS!  Do you have another machine that you can connect at least one of the drives to see if it even reads that drive?

Otherwise, try running these commands from a terminal.

```
lsusb
dmesg | tail
```

---

### Post by utnubuuser on 2009-03-13
Found a thread about forcing a frozen system to shutdown:> [http://ubuntuforums.org/showthread.php?t=1094795](http://ubuntuforums.org/showthread.php?t=1094795)

---

### Post by CarolinaGuy on 2009-03-13
```
charlie@ubuntu8:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Bus 001 Device 003: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 001 Device 002: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 001 Device 001: ID 0000:0000

```

```

charlie@ubuntu8:~$ dmesg | tail
[   65.521971] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   73.859696] eth0: no IPv6 routers present
[   97.306796] EXT3 FS on sda1, internal journal
[   97.677131] kjournald starting.  Commit interval 5 seconds
[   97.677149] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   97.677368] EXT3 FS on sda3, internal journal
[   97.677376] EXT3-fs: mounted filesystem with ordered data mode.
[   98.574599] ip_tables: (C) 2000-2006 Netfilter Core Team
[  100.340763] ppdev: user-space parallel port driver
[  100.792870] audit(1236917523.694:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4586 profile="/usr/sbin/cupsd" namespace="default"
charlie@ubuntu8:~$

```
I do have other system I can plug the drive into; but, I'll do that first things tomorrow, to late here in NC to dig into that now. 

What's this?? don't recall setting up any ip_tables.
[   98.574599] ip_tables: (C) 2000-2006 Netfilter Core Team


CarolinaGuy

---

### Post by CarolinaGuy on 2009-03-13
Taurus - utnubuuser

This seems to be a hardware problem. After shutting down at around midnight last night; the computer found all hard drives and booted find. I can access all my samba shares with no problem. I NOW believed I have a secondary IDE channel problem. This is an old MB - Asus A7N266-c with an Athlon 1700+ installed. I'll see if I can flash thee bios and update it.

```

charlie@ubuntu8:~$ sudo fdisk -l
[sudo] password for charlie:
Sorry, try again.
[sudo] password for charlie:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040edd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7079    56862036   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda3            7080        9541    19776015   83  Linux
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d4fec2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           28942       60801   255915450   83  Linux
/dev/sdb2               1       28941   232468551   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008f5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

```

CarolinaGuy

---

