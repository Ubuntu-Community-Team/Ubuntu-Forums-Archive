---
title: "Auto-Mounting of Drives on Start-Up?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-12-27
Ubuntu is great, but it's not without its minor irritations.

One that really irks me is the need to mount one's NTFS drives before running an app that references files stored there.

Take as an example a music library app such as Amarok. All of my mp3 and wma files are stored on an NTFS drive so that on the rare occasion I use Windoze, I have access to them. But I can't simply boot up and run Amarok expecting it to find my files - I have to mount the appropriate drive and then run Amarok. It's only a couple of clicks, but it's becoming a pain.

As another example, I store all of my emails on an NTFS drive, so that I can read and manipulate them on either Thunderbird in Ubuntu or Thunderbird in Windoze. So I have to mount the drive before launching Thunderbird, or else I don't see any emails at all.

So, my question is, is there some script I could add to my Ubuntu start-up code that does "look for all available NTFS drives and mount all of them"?

To be honest, I really don't know why such a configuration isn't in Ubuntu by default, as surely the only time one wants one's drives to be unmounted is when doing an initial installation, isn't it?

---

### Post by nhasian on 2008-12-27
follow this guide to have your ntfs partitions auto-mounted at startup:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29)

---

### Post by jerome1232 on 2008-12-27
Basically you just need to add them to your fstab, for ntfs drive I hear ntfs-config is a good gui for doing this, I've never used it though.

```
sudo apt-get install ntfs-config
```

If you wanted help manually adding them to fstab instead of using that gui then post the output of these commands and I can get you going with that.
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by thbrowns on 2008-12-27
> **jerome1232 said:**
> for ntfs drive I hear ntfs-config is a good gui for doing this

I can recommend ntfs-config. Have just used it myself to automount my ntfs share drive.

---

### Post by maddog39 on 2008-12-27
Wikipedia has a good article on the explanation of the /etc/fstab file and explains all the parameters for each line.

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

---

### Post by Norm24 on 2008-12-27
Having used ntfs-config to automount now I can't unmount my ntfs partition at all!I no longer have privliledges to do so! 

How do I ummount the partition?

---

### Post by jerome1232 on 2008-12-27
Well from the command line you unmount like this, change sdxx to the real device or /path/to/mount/point to the real mount point.

```
sudo umount /dev/sdxx
### or
sudo umount /path/to/mount/point
```

---

### Post by Norm24 on 2008-12-27
> **jerome1232 said:**
> Well from the command line you unmount like this, change sdxx to the real device or /path/to/mount/point to the real mount point.

```
sudo umount /dev/sdxx
### or
sudo umount /path/to/mount/point
```

That's beyond my technical understanding.

Basically how do I stop the automounting of the partition and remove the mount point?

---

### Post by Roger Allott on 2008-12-27
> **jerome1232 said:**
> 
If you wanted help manually adding them to fstab instead of using that gui then post the output of these commands and I can get you going with that.
```
sudo fdisk -l
cat /etc/fstab
```

Cheers, that would be great.

**output of command:** sudo fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x509ee0a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda4           13567       19458    47314944    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         262     2104483+  82  Linux swap / Solaris
/dev/sdb2   *         263        2873    20972857+  83  Linux
/dev/sdb3            2874        3355     3871665   83  Linux
/dev/sdb4            3356        9729    51199155    7  HPFS/NTFS
```


**output of command:** cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9c3e50c8-03f0-4efc-8bc7-74ada71c8651 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=e8714d41-bba5-4764-bb96-957fa7b188a1 /home           ext3    relatime        0       2
# /dev/sda1
UUID=7551d527-6cc4-4f42-9f68-7d2cead50e3c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by jerome1232 on 2008-12-27
Okay from the output of fdisk

/dev/sda2
/dev/sda4
/dev/sdb4

are the ntfs partitions in question. I actually forgot something can you post one more thing.

```
sudo blkid
```

---

### Post by Roger Allott on 2008-12-27
> **jerome1232 said:**
> Okay from the output of fdisk

/dev/sda2
/dev/sda4
/dev/sdb4

are the ntfs partitions in question. I actually forgot something can you post one more thing.

```
sudo blkid
```

output:
```
/dev/sda1: UUID="A2401BBF401B995D" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="CEA61E2BA61E1515" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda4: UUID="DC0E219E0E2172A6" TYPE="ntfs" LABEL="DATA" 
/dev/sdb1: TYPE="swap" UUID="7551d527-6cc4-4f42-9f68-7d2cead50e3c" 
/dev/sdb2: UUID="9c3e50c8-03f0-4efc-8bc7-74ada71c8651" TYPE="ext3" 
/dev/sdb3: UUID="e8714d41-bba5-4764-bb96-957fa7b188a1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="7F2A3353027874FC" TYPE="ntfs" 
```

---

### Post by jerome1232 on 2008-12-27
Okay basically just add everything below ### NTFS DISKS to your fstab
```
gksu gedit /etc/fstab
```

If you look over everything carefully you should get a good idea of what I did, this is also a good how to if you want to learn more about fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

the 'user' option should give you permission to unmount the volumes using the gui. MIGHT need to change that to 'users' I'm not sure. umask=000 makes the drive readable/writable by any user on the system. the last two zero's tell linux to never check these drives during the boot process.

cheers.

---edit--- you'll need to create those new directories

```
sudo -i
mkdir /media/system
mkdir /media/WinRE
mkdir /media/data
mkdir /media/sdb4
```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9c3e50c8-03f0-4efc-8bc7-74ada71c8651 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=e8714d41-bba5-4764-bb96-957fa7b188a1 /home           ext3    relatime        0       2
# /dev/sda1
UUID=7551d527-6cc4-4f42-9f68-7d2cead50e3c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
### NTFS DISKS
# SYSTEM
UUID=CEA61E2BA61E1515 /media/system ntfs-3g user,umask=000 0 0
# WinRE
UUID=A2401BBF401B995D /media/WinRE ntfs-3g user,umask=000 0 0
# DATA
UUID=DC0E219E0E2172A6 /media/data ntfs-3g user,umask=000 0 0
# /dev/sdb4
UUID=7F2A3353027874FC /media/sdb4 ntfs-3g user,umask=000 0 0
```

---

### Post by Roger Allott on 2008-12-27
Thanks for that jerome1232.

I've just rebooted and, low and behold, all drives were mounted!

One slight discrepancy was that 'system' should have been 'SYSTEM', 'data' should have been 'DATA', and 'sdb4' should have been 'disk'.

However, you weren't to know that, and it was pretty simple to amend the folder locations in Amarok & Thunderbird.

---

