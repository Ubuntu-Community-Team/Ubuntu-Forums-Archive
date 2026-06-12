---
title: "does my cd drive exist? cannot mount it!"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by abben on 2010-02-22
I've done a pretty bare-bones install, I'm using lightweight programs and all that jazz. Maybe it's something I did, but on this new install I can't seem to mount my cdrom.

My /etc/fstab file says this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

and if I understand this correctly, that should correspond to the primary slave in my bios, right? 

```
sudo mount /dev/hdb
mount: special device /dev/hdb does not exist
```

Am I doing something wrong? Should I change to secondary slave maybe?

**Edit:** I'm adding a part of my huge dmesg output. It doesn't look like my cd-rom is getting picked up. 

```
dmesg | grep hd
[    4.140901] hda: ST380011A, ATA DISK drive
[    4.813241] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[    4.813558] hda: UDMA/33 mode selected
[    5.232660] hda: max request size: 512KiB
[    5.245383] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63
[    5.245582] hda: cache flushes supported
[    5.245987]  hda: hda1 hda2 < hda5 >
[   12.533789] Adding 176672k swap on /dev/hda5.  Priority:-1 extents:1 across:176672k 
[   12.827012] EXT3 FS on hda1, internal journal
```

---

### Post by theDaveTheRave on 2010-02-23
abben,

first off I think you may need to add some details to the cdrom line in your fstab.

here is the line in my fstab...

```


/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

check out the [fstab wiki page]("https://help.ubuntu.com/community/Fstab"), I have used it a lot to get my ststem(s) to work correctly, and also the [forum page]("http://ubuntuforums.org/showthread.php?t=283131").

David

---

### Post by abben on 2010-02-23
Thanks for the response, however I think my problem precedes any fstab issues. My relevant fstab line:

```
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

assumes that a device called /dev/hdb exists (which it should). However, I cannot find any /dev/hdb. 

For instance, the wiki page you linked me to says I should us the **blkid** command to find the UUID of each device. But when I run that...

```
sudo blkid
/dev/hda5: TYPE="swap" 
/dev/hda1: UUID="94df0707-51b1-4253-9e0f-f18c417ac507" TYPE="ext3"
```

.. it shows just my hard drive. (Is it *supposed* to show my cd drive if it exists?) If I do **fdisk -l**....


```
sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8ad0

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9707    77971446   83  Linux
/dev/hda2            9708        9729      176715    5  Extended
/dev/hda5            9708        9729      176683+  82  Linux swap / Solaris

```

Again, I'm not sure if that's *supposed* to show my device, but I think it is. If I do **mount**...

```
mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)

```

If I do **dmesg**...

```
dmesg | grep hd
[    4.039906] hda: ST380011A, ATA DISK drive
[    4.712083] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[    4.712611] hda: UDMA/33 mode selected
[    5.150380] hda: max request size: 512KiB
[    5.160053] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63
[    5.160264] hda: cache flushes supported
[    5.160667]  hda: hda1 hda2 < hda5 >
[   13.452449] Adding 176672k swap on /dev/hda5.  Priority:-1 extents:1 across:176672k 
[   13.747460] EXT3 FS on hda1, internal journal
```

So, I think, long before I can even judge the correctness of my fstab file, I have to be able to actually detect the device. Once I can find it, I can discover whether my cdrom is actually /dev/hdb like fstab thinks it is (or give the correct uuid or...). Supposing my cdrom is actually plugged in (it ought to be, I've booted from it several times), is there any command I can do just to see if linux detects the device?

---

### Post by theDaveTheRave on 2010-02-24
abben,

sorry, maybe the wiki page isn't a 'good' as the [forum pages]("http://ubuntuforums.org/showthread.php?t=283131") try the following to hopfully list ALL the devices connected to your system.

They shouldn't need to be 'mounted', they certainly didn't on my system!



```

ls /dev/disk/by-label -alh

```
Good if you have a cd/dvd in the drive as the "title" of the disk will be displayed, for example here is my output...
```

$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root  60 2010-02-24 09:27 .
drwxr-xr-x 6 root root 120 2010-02-24 09:27 ..
lrwxrwxrwx 1 root root   9 2010-02-24 09:27 BBCDVD1120 -> ../../sr0

```
which also tells me the device is <../../sro (it is a dvd from the BBC).

Note that this doesn't show the HDD, to get those as well use the following... [my output included for reference]

```

$ ls /dev/disk/by-path -lah
total 0
drwxr-xr-x 2 root root 200 2010-02-24 09:26 .
drwxr-xr-x 6 root root 120 2010-02-24 09:27 ..
lrwxrwxrwx 1 root root   9 2010-02-24 09:26 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  10 2010-02-24 09:26 pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2010-02-24 09:26 pci-0000:00:1f.2-scsi-0:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 2010-02-24 09:26 pci-0000:00:1f.2-scsi-0:0:0:0-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 2010-02-24 09:26 pci-0000:00:1f.2-scsi-0:0:0:0-part7 -> ../../sda7
lrwxrwxrwx 1 root root  10 2010-02-24 09:26 pci-0000:00:1f.2-scsi-0:0:0:0-part8 -> ../../sda8
lrwxrwxrwx 1 root root  10 2010-02-24 09:26 pci-0000:00:1f.2-scsi-0:0:0:0-part9 -> ../../sda9
lrwxrwxrwx 1 root root   9 2010-02-24 09:26 pci-0000:00:1f.2-scsi-1:0:0:0 -> ../../sr0

```

As I say earlier, maybe the forum thread is a better option for getting help with your problem, rather than the wiki? sorry for that...

David.

---

