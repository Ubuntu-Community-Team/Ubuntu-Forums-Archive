---
title: "Walkthrough required - change mount locations, permissions, and set to mount at boot"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-11-19
Hi all

I did a clean install of Karmic and am sitting with the same head scratcher I always have after upgrades.

I have 2 physical harddrives, the first contains WinXP and Karmic.  The second contains 3 partitions - 1 Ext3, 1 FAT32, 1 NTFS.

At present all partitions on the 2nd drive require a password before mounting and all mount to /media.

In my jaunty install I had all automounted to /mnt at startup, with no problems with permissions - I'd like to do this again.

No idea where to start though. Vaguely remember fstab or something.  Any help is appreciated.

Cheers

---

### Post by nothingspecial on 2009-11-19
sudo blkid to find the UUID`s of the different partitions, then add them to /etc/fstab like so

```
UUID=b80dc834-e5ed-423c-8538-0fb448d0d34c /media/music    ext3    relatime,noexec  0       2
UUID=48e6d536-a3dc-4d59-88a0-1d291cb1bb27 /media/backup   ext3    relatime,noexec  0       2
```

---

### Post by aquascrotum on 2009-11-19
sudo blikd gets me "sudo: blikd: command not found"....?

---

### Post by sisco311 on 2009-11-19
> **aquascrotum said:**
> sudo blikd gets me "sudo: blikd: command not found"....?

it's:
```
sudo **blkid**
```

or
```
ls -al /dev/disk/by-uuid/
```

```
lrwxrwxrwx 1 root root  10 Nov 19 07:50 [COLOR="Red"]82ad448c-acce-45bb-a023-8be0e88b9ff7[/COLOR] -> ../../[COLOR="Blue"]sda4[/COLOR]
```

[color="red"]uuid[/color]
[color="Blue"]partition[/color]

---

### Post by sisco311 on 2009-11-19
to mount the fat and ntfs partitions, instead of relatime,noexec use the following mount options:
```
defaults,gid=plugdev,dmask=002,fmask=113
```

this will set the ownership and permissions as follow:
owner: root
group: plugdev

read/write/execute permission for root and users in the plugdev group (directories) 

(execute allows changing into the directory, i.e. cd command)

read/write permission for root and users in the plugdev group (files)

read/execute for others (directories)
read for others (files)

[uhelp]community/FilePermissions[/uhelp]

And instead of ext3 use vfat and ntfs for the filesystem type.

to add a user to the plugdev group:
```
sudo adduser username plugdev
```

---

### Post by aquascrotum on 2009-11-19
> **sisco311 said:**
> it's:
```
sudo **blkid**
```

or
```
ls -al /dev/disk/by-uuid/
```

```
lrwxrwxrwx 1 root root  10 Nov 19 07:50 [COLOR="Red"]82ad448c-acce-45bb-a023-8be0e88b9ff7[/COLOR] -> ../../[COLOR="Blue"]sda4[/COLOR]
```

[color="red"]uuid[/color]
[color="Blue"]partition[/color]

I've got my blkid now (thanks for that), as follows:

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0606" TYPE="vfat" 
/dev/sda2: UUID="603893EF3893C308" LABEL="WinXP OS" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" TYPE="vfat" 
/dev/sda5: UUID="3b2c5929-7779-494b-aaa9-d8af19592851" TYPE="ext4" 
/dev/sda6: UUID="5a6a6597-5c90-4660-9e04-a75bea950e37" TYPE="swap" 
/dev/sdb5: LABEL="iTunes" UUID="49CF-6DFB" TYPE="vfat" 
/dev/sdb6: UUID="4FB7F05A089D3BBA" LABEL="WinXP - Linux Swap" TYPE="ntfs" 
/dev/sdb7: LABEL="KyleLinux" UUID="17689df7-d68d-4fd8-8831-5d0dc6b56202" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="2CE4F2D1E4F29BF0" LABEL="Buffalo Media" TYPE="ntfs"
``` 

I created my desired mount points for each partition in /mnt/... I've had an initial stab at editing my fstab but all 3 partitions have gone missing after rebooting.

Output from fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=3b2c5929-7779-494b-aaa9-d8af19592851 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5a6a6597-5c90-4660-9e04-a75bea950e37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=49CF-6DFB	/mnt/itunes	vfat	user,noauto,exec,utf8	0	0
UUID=4FB7F05A089D3BBA	/mnt/linux-xp	ntfs	user,noauto,exec,utf8	0	0
UUID=17689df7-d68d-4fd8-8831-5d0dc6b56202	/mnt/kyle-linux	user,noauto,exec,utf8	0	0

In terms of the options I'm applying there I've no idea what I'm doing tbh, I just copied them from the cdrom permissions.

---

### Post by falconindy on 2009-11-19
Copying options from a cd-rom drive for a hard drive isn't ideal. I would use something such as:

```
defaults,noatime
```

In case you're curious, defaults expands to:
```
rw,suid,dev,exec,auto,nouser,async
```

If you'd prefer to have access dates, use relatime instead of noatime. Notice its **relatime** and not **realtime**.

edit: I should read partition types before i post.. see below instead.

---

### Post by sisco311 on 2009-11-19
```
UUID=49CF-6DFB /mnt/itunes vfat defaults,gid=plugdev,dmask=002,fmask=113 0 0

UUID=4FB7F05A089D3BBA /mnt/linux-xp ntfs defaults,gid=plugdev,dmask=002,fmask=113 0 0

UUID=17689df7-d68d-4fd8-8831-5d0dc6b56202 /mnt/kyle-linux ext3 relatime 0 2
```


EDIT: you dont have to reboot to mount the partitions, just run:
```
sudo mount -a
```

mount -a = mount all partitions listed in fstab.

---

### Post by aquascrotum on 2009-11-19
> **sisco311 said:**
> ```
UUID=49CF-6DFB /mnt/itunes vfat defaults,gid=plugdev,dmask=002,fmask=113 0 0

UUID=4FB7F05A089D3BBA /mnt/linux-xp ntfs defaults,gid=plugdev,dmask=002,fmask=113 0 0

UUID=17689df7-d68d-4fd8-8831-5d0dc6b56202 /mnt/kyle-linux ext3 relatime 0 2
```


EDIT: you dont have to reboot to mount the partitions, just run:
```
sudo mount -a
```

mount -a = mount all partitions listed in fstab.

Genuinely, thanks a million!!  Worked a treat.  You've done your good deed for the day ;)

---

### Post by sisco311 on 2009-11-19
> **aquascrotum said:**
> Genuinely, thanks a million!!  Worked a treat.  You've done your good deed for the day ;)

Cool!!! And it's only 00:55 AM here. :)

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

Thanks!

---

### Post by bodhi.zazen on 2009-11-19
FYI :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

You can do it with a GUI tool : [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

pysdm is in the repos.

---

### Post by sisco311 on 2009-11-19
> **bodhi.zazen said:**
> FYI :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

You can do it with a GUI tool : [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

pysdm is in the repos.

[s]does pysdm uses uuids to create the fstab entry?[/s]

Never mind, it still uses /dev/dsXY which is no longer preferred since these device assignments can change between system boots.

---

### Post by bodhi.zazen on 2009-11-19
> **sisco311 said:**
> [s]does pysdm uses uuids to create the fstab entry?[/s]

Never mind, it still uses /dev/dsXY which is no longer preferred since these device assignments can change between system boots.

You raise a good point.

You may use uuid with psydm, but the mount points are then named by uuid, so they are ugly :p

pysdm is , IMO, most helpful for fixed (usually internal) drives as these are most commonly the ones used in fstab entries (most people do not write a fstab entry fo rflash drives).

:popcorn:

---

### Post by sisco311 on 2009-11-19
> **bodhi.zazen said:**
> You raise a good point.

You may use uuid with psydm, but the mount points are then named by uuid, so they are ugly :p

pysdm is , IMO, most helpful for fixed (usually internal) drives as these are most commonly the ones used in fstab entries (most people do not write a fstab entry fo rflash drives).

:popcorn:

Unfortunately, also fixed drives can end up with a different device names after a reboot. It's not so common but it happens. 


And yes, in pysdm, you can refer to the partition by the uuid in the name section, but in the fstab entry the device name will be still /dev/sdXY (at least in Lucid Lynx).

---

