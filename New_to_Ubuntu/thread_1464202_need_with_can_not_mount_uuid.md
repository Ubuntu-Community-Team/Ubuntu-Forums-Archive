---
title: "need with can not mount uuid"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by maldonw on 2010-04-27
hello all 
first let me say that I am brand new at ubuntu I mean like 5 days new. I recently installed uduntu on my vista laptop with no issue whatsoever but as luck would have it my hard drive kicked the bucket yesterday. after I copied the image of the old hard drive to the new one and when i booted up in ubuntu i get this error.

/etc/fstab cannot be mounted waiting for UUID = fca4e6d9-350d-4f7f-ba51-ab314463b340

after hours of serching I believe the issue is my uuid for the new drive is different than the old. but for the life of me i don't know how to correct it and the posts i have seen that show you how are a bit beyond my knowledge at this point and finding a step by step tutorial seems a bit difficult. below is what i see when i used the blkid command

[COLOR=Red]
wilfredo@wilfredo-laptop:~$ blkid
/dev/sda1: UUID="20378F114179A3DD" TYPE="ntfs" 
/dev/sda2: UUID="748888D7888898EE" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="08b535cc-94eb-461c-bc15-d1d30a8cd5a0" TYPE="ext4" 
/dev/sda6: TYPE="swap" 
wilfredo@wilfredo-laptop:~$ [/COLOR]


When i use the sudo nano /etc/fstab command that i read online i get this output

[COLOR=Red]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=08b535cc-94eb-461c-bc15-d1d30a8cd5a0 /               ext4    errors=remoun$
# swap was on /dev/sda6 during installation
UUID=fca4e6d9-350d-4f7f-ba51-ab314463b340 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


[/COLOR]Can anyone see whats wrong and can someone give me the idiots guide on how to fix this. 
Thank you very much in advance

---

### Post by Bachstelze on 2010-04-27
Please also run

```
ls -l /dev/disk/by-uuid
```

blkid didn't show the UUID for your swap partition, for some reason.

---

### Post by maldonw on 2010-04-28
> **Bachstelze said:**
> Please also run

```
ls -l /dev/disk/by-uuid
```blkid didn't show the UUID for your swap partition, for some reason.


Here is what comes up

[COLOR=Red]wilfredo@wilfredo-laptop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-04-28 04:31 08b535cc-94eb-461c-bc15-d1d30a8cd5a0 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-04-28 04:31 20378F114179A3DD -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-04-28 04:31 748888D7888898EE -> ../../sda2
wilfredo@wilfredo-laptop:~$ [/COLOR]

---

### Post by Bachstelze on 2010-04-28
This is very weird, the swap partition doesn't show up... How about

```
sudo fdisk -l
```

---

### Post by maldonw on 2010-04-28
> **Bachstelze said:**
> This is very weird, the swap partition doesn't show up... How about

```
sudo fdisk -l
```

here you go
[COLOR=Red]
wilfredo@wilfredo-laptop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a339b80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       55079   442422036    7  HPFS/NTFS
/dev/sda2           56510       57619     8916075    7  HPFS/NTFS
/dev/sda3           55080       56509    11486475    5  Extended
/dev/sda5           55080       56443    10956298+  83  Linux
/dev/sda6           56444       56509      530113+  82  Linux swap / Solaris

Partition table entries are not in disk order[/COLOR]

---

### Post by Leppie on 2010-04-28
I'm not sure if these were typos, but you've got some dollar signs I've never seen in any fstab:
```
[COLOR=Black]# / was on /dev/sda5 during installation
UUID=08b535cc-94eb-461c-bc15-d1d30a8cd5a0 /               ext4    errors=remoun_**[COLOR=Red]$[/COLOR]**_
# swap was on /dev/sda6 during installation
UUID=fca4e6d9-350d-4f7f-ba51-ab314463b340 none            swap    sw           _**[COLOR=Red]$[/COLOR]**_[/COLOR]
```

you  may want to change these entries to something like this:
```
[COLOR=Black]# / was on /dev/sda5 during installation
UUID=08b535cc-94eb-461c-bc15-d1d30a8cd5a0 /               ext4    errors=remoun_**[COLOR=Red]t[/COLOR]**_
# swap was on /dev/sda6 during installation
UUID=fca4e6d9-350d-4f7f-ba51-ab314463b340 none            swap    sw[/COLOR]
```

---

### Post by maldonw on 2010-04-28
> **Leppie said:**
> I'm not sure if these were typos, but you've got some dollar signs I've never seen in any fstab:
```
[COLOR=Black]# / was on /dev/sda5 during installation
UUID=08b535cc-94eb-461c-bc15-d1d30a8cd5a0 /               ext4    errors=remoun_**[COLOR=Red]$[/COLOR]**_
# swap was on /dev/sda6 during installation
UUID=fca4e6d9-350d-4f7f-ba51-ab314463b340 none            swap    sw           _**[COLOR=Red]$[/COLOR]**_[/COLOR]
```you  may want to change these entries to something like this:
```
[COLOR=Black]# / was on /dev/sda5 during installation
UUID=08b535cc-94eb-461c-bc15-d1d30a8cd5a0 /               ext4    errors=remoun_**[COLOR=Red]t[/COLOR]**_
# swap was on /dev/sda6 during installation
UUID=fca4e6d9-350d-4f7f-ba51-ab314463b340 none            swap    sw[/COLOR]
```


The reason for the dollar signs was that the window was not wide enough here is the same code again in a wider window

[COLOR=Red]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=08b535cc-94eb-461c-bc15-d1d30a8cd5a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fca4e6d9-350d-4f7f-ba51-ab314463b340 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


[/COLOR]

---

### Post by maldonw on 2010-04-28
from what I have read If I understand it my swap drive has no UUID and from what I have read I can use uuidgen to make a new one but how do i change the uuid so that it will stop looking at the uuid that is no longer there and assign the drive with a new one. Unless I am totally wrong in what I assume is the problem:confused:

---

### Post by Elfy on 2010-04-28
once you have the UUID - open fstab as root and edit the swap line to suit the new number 

```
gksudo gedit /etc/fstab
```

You can check that it will work with

```
sudo swapon -a
```

Never used uuidgen but it looks like 
```

sudo tune2fs -U uuidgen /dev/sda6
``` should do it - might be worth checking that last one.

---

### Post by bab1 on 2010-04-28
> **forestpiskie said:**
> once you have the UUID - open fstab as root and edit the swap line to suit the new number 

```
gksudo gedit /etc/fstab
```

You can check that it will work with

```
sudo swapon -a
```

Never used uuidgen but it looks like 
```

sudo tune2fs -U uuidgen /dev/sda6
``` should do it - might be worth checking that last one.

Or use the original one again.```
 sudo tune2fs -U fca4e6d9-350d-4f7f-ba51-ab314463b340 /dev/sda6
```

No need to edit the fstab file.

---

### Post by maldonw on 2010-04-28
> **forestpiskie said:**
> once you have the UUID - open fstab as root and edit the swap line to suit the new number 

```
gksudo gedit /etc/fstab
```You can check that it will work with

```
sudo swapon -a
```Never used uuidgen but it looks like 
```

sudo tune2fs -U uuidgen /dev/sda6
``` should do it - might be worth checking that last one.

tried the following commands and got these errors:

[COLOR=Red]wilfredo@wilfredo-laptop:~$ sudo tune2fs -U fca4e6d9-350d-4f7f-ba51-ab314463b340 /dev/sda6
tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sda6
Couldn't find valid filesystem superblock.
[/COLOR]
also tried this suggestion:

  	 	 	 	 	 	  [COLOR=Red]wilfredo@wilfredo-laptop:~$ sudo tune2fs -U uuidgen /dev/sda6 [/COLOR]
 [COLOR=Red]tune2fs 1.41.9 (22-Aug-2009) [/COLOR]
 [COLOR=Red]tune2fs: Bad magic number in super-block while trying to open /dev/sda6 [/COLOR]
 [COLOR=Red]Couldn't find valid filesystem superblock. [/COLOR]
 [COLOR=Red]wilfredo@wilfredo-laptop:~$  [/COLOR]
 [COLOR=Red]
[COLOR=Black]something i noticed not sure if it matters is when I use the blkid command the swap has no UUID however when i view the /etc/fstab file it does show a UUID. not sure if that is releveant check my above posts to see what i mean. [/COLOR]
[/COLOR]

---

### Post by Leppie on 2010-04-28
you could delete the swap and then recreate it. if the new one is in the same place and has the same size, the uuid should be the same.
or if you never use swap (because you've got plenty of ram and you don't use hibernate) you can leave out the swap partition altogether.

---

