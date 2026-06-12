---
title: "Need FSTAB/Mounting Help Please!"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by ghostofzuul on 2009-01-11
Hi. 

So i have a hard drive for back-up purposes formatted and partitioned using vfat. When I first restarted the machine with the drive installed  it seemed to be recognized as a removable drive and I could access it. I got a dialog about mount points and when I went to mount the volume, I must have filled out one of the tabs wrong b/c now I can't mount. 

here's the listing from my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e74f8958-2ed5-4232-b3ec-99a69ca5d783 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=78BB-1DE9 /media/sdb1 vfat defaults 0 2        
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Strangely in my most recent attempt to mount the volume, I got the error message

"You are not privileged to mount the volume 'backup' "

I'm only two days into this linux project so any help would be greatly appreciated.

Thanks!

---

### Post by taurus on 2009-01-11
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
df -h
```

---

### Post by ghostofzuul on 2009-01-11
hello.  

 sudo fdisk -l

Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00082474

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3580    28756318+  83  Linux
/dev/sda2            3581        3739     1277167+   5  Extended
/dev/sda5            3581        3739     1277136   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39062457    b  W95 FAT32


and

sudo blkid df -h
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghl] [-o format] [-s <tag>] [-t <token>]
    [-v] [-w <file>] [dev ...]
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)

---

### Post by taurus on 2009-01-11
> **ghostofzuul said:**
> hello.  

 sudo fdisk -l

Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00082474

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3580    28756318+  83  Linux
/dev/sda2            3581        3739     1277167+   5  Extended
/dev/sda5            3581        3739     1277136   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39062457    b  W95 FAT32


and

**[COLOR="DarkRed"]sudo blkid df -h[/COLOR]**
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghl] [-o format] [-s <tag>] [-t <token>]
    [-v] [-w <file>] [dev ...]
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)

That should be two separate commands.

```
sudo blkid  <-- Return
df -h  <-- Return
free -m  <-- Return
```

---

### Post by ghostofzuul on 2009-01-11
> **taurus said:**
> That should be two separate commands.

```
sudo blkid  <-- Return
df -h  <-- Return
free -m  <-- Return
```

told you i was green... thanks for your patience. :)

sudo blkid
/dev/sda1: UUID="e74f8958-2ed5-4232-b3ec-99a69ca5d783" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b84ceac4-9399-4fbd-813b-0e34889a799f" 
/dev/sdb1: LABEL="ZUULBACKUP" UUID="78BB-1DE9" TYPE="vfat" 


 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              28G  3.2G   23G  13% /
varrun                252M  212K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   56K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   39M  213M  16% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon       28G  3.2G   23G  13% /home/stormy/.gvfs


free -m
             total       used       free     shared    buffers     cached
Mem:           502        458         43          0         14        253
-/+ buffers/cache:        191        311
Swap:            0          0          0


thx

---

### Post by taurus on 2009-01-11
Couple  of things.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it for your swap partition.  As of right now, swap partition (/dev/sda5) is not in used.

```

UUID=b84ceac4-9399-4fbd-813b-0e34889a799f   none   swap   sw   0   0
```
Then, modify the entry for /dev/sdb1 from this

```
UUID=78BB-1DE9 /media/sdb1 vfat defaults 0 2 
```
to this.

```

/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000  0  0
```
Save the changes and close down the gedit editing windows.  Now run

```
sudo mount -a
df -h
free -m
```

---

### Post by ghostofzuul on 2009-01-11
hi thanks again... i edited the file as per your suggestion, I think I got it right:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e74f8958-2ed5-4232-b3ec-99a69ca5d783 /               ext3    relatime,errors=remount-ro 0       1
/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000  0  0       
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=b84ceac4-9399-4fbd-813b-0e34889a799f   none   swap   sw   0   0

however i get this error when using command mount -a:

root@DRFUNKENSTEIN:~# mount -a
mount: mount point /media/sdb1 does not exist

---

### Post by taurus on 2009-01-11
You need to create the mount point for your second harddrive first before you can mount to it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h 
free -m
```

---

### Post by ghostofzuul on 2009-01-11
SOLVED!

Thanks. 

You make it look easy. I've got to get a good linux book.

I've got one other problem that's vexing... I'll make a new post in a bit probably a piece of cake for us non-newbies...

Thanks again!

---

### Post by ghostofzuul on 2009-01-11
I can access the hard drive now, although I can see the drive on my network. I have access to the files that I've listed as "shared folders" but when I tried to share the /media/sdb1 directory i received this msg:

'net usershare' returned error 255: net usershare add: cannot share path /media/sdb1 as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.


looked in smb.conf... not sure where to ad the line...

thanks again..

---

