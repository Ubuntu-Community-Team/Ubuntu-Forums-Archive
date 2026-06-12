---
title: "problem with mounting"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by megayo on 2008-12-21
I been searching around the site and didn't found a solution for my problem...
right now I have 5 disks
1 Linux ext3
3 ntfs 
1 fat (with windows on it)

I've installed psydm for managing my hard drive

and I configured some of the hard drivers,now when I tried to mount or unmount - some of them works and some don't.
In order to fix that I uninstall completely the pysdm and steel the problem remain

1 of the ntfs and the fat are working just fine.

But the other 2 ntfs just doesn't mount/unmount (only those two [the 2 ntfs] mounting automatically on startup but the other two [the ntfs & the fat] aren't)

by the way here's my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda7
UUID=567c59b5-7109-454e-8023-7e8190e57e53  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda8
UUID=30a84c7e-1978-4668-bbee-e511d8c3c94d  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda5                                  /media/sda5    ntfs         defaults                    0  0  
/dev/sda8                                  /media/sda8    ntfs         defaults                    0  0  
/dev/sda1                                  /media/sda1    vfat         users,noauto,user           0  0  

```

thanks in advance
p.s. sorry for my poor english

---

### Post by Dedoimedo on 2008-12-21
Hi,

Can you please tell which ones start and which ones don't?
Can you please post the contents of: sudo fdisk -l ?
Can you please try to mount the drives manually from the command line, one by one:

sudo mount -t ntfs-3f /dev/<device> /mnt

And for fat: sudo mount -t vfat /dev/<device> /mnt

Let's see what comes up.

Dedoimedo

---

### Post by megayo on 2008-12-21
1.sda8 & sda5 start on startup
sda1 dosent & i'm not sure which one is the other working ntfs but i _think_ it scd0 
(by the way i didnt configure the working ntfs with pysdm)

2.```
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc63cc63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   c  W95 FAT32 (LBA)
/dev/sda2            1913        9732    62814150    f  W95 Ext'd (LBA)
/dev/sda5            1913        2304     3148708+   7  HPFS/NTFS
/dev/sda6            2305        4856    20498908+  83  Linux
/dev/sda7            7557        7649      746991   82  Linux swap / Solaris
/dev/sda8            7650        9732    16731666    7  HPFS/NTFS
/dev/sda9            4857        7556    21687718+   7  HPFS/NTFS

Partition table entries are not in disk order

```

i tried to mount wite the terminal it didnt do anything it just wrote my:  
```
~$ sudo mount -t ntfs-3f /dev/scd0/mnt
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

---

### Post by megayo on 2008-12-21
bump already page 3?!

edit:
maybe i'll put it this way.how can i reverse the pysdm changes?

---

### Post by Dedoimedo on 2008-12-21
Hello,

I wrote you the exact commands to use:

NTFS:
sudo mount -t ntfs-3g /dev/sdX /mnt

FAT32:
sudo mount -t vfat /dev/sdX /mnt

sda1 is fat, sda5,8,9 are ntfs. Try manually, one by one using the above commands.

Dedoimedo

---

### Post by megayo on 2008-12-21
> **Dedoimedo said:**
> Hello,

I wrote you the exact commands to use:

NTFS:
sudo mount -t ntfs-3g /dev/sdX /mnt

FAT32:
sudo mount -t vfat /dev/sdX /mnt

sda1 is fat, sda5,8,9 are ntfs. Try manually, one by one using the above commands.

Dedoimedo
manually it unmount one of them(sda5) the other just wont unmount (i tried sad9 sda0 scd9 scd0)!

but when I mount it back it doesn't shows up anywhere not even on the removable media...(when i unmounted it - it shows up again...)

---

