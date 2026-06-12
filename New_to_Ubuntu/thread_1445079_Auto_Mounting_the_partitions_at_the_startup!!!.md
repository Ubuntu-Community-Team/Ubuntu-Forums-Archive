---
title: "Auto Mounting the partitions at the startup!!!"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-04-02
how to auto mount the partitions at the start in kubuntu???

---

### Post by Elfy on 2010-04-02
In the same way that you were advised before - [http://ubuntuforums.org/showthread.php?t=1392530](http://ubuntuforums.org/showthread.php?t=1392530)

I edit fstab manually to do what I want - but pysdm as advised in that thread does the same thing.

---

### Post by 1991sudarshan on 2010-04-02
> **forestpiskie said:**
> In the same way that you were advised before - [http://ubuntuforums.org/showthread.php?t=1392530](http://ubuntuforums.org/showthread.php?t=1392530)

I edit fstab manually to do what I want - but pysdm as advised in that thread does the same thing.

those methods seem to be very tedious and confusing! is there are any other easy method to do it???

---

### Post by Elfy on 2010-04-02
pysdm is the easy way - I do not know of an easier way.

Once it is done it does not need to be done again.

I have the same fstab that I have used for 2 years - with a few additions as drives get added.

---

### Post by Morbius1 on 2010-04-02
This is the way it was done in the olden days. Maybe it's because it's the way I've always done it but I really don't see why this is considered so difficult :wink:

It's really a set of three templates:

***STEP 1: Find out how the system sees your partitions***

Open **Terminal**
Type **sudo blkid -c /dev/null**

This will output , among other things the following partitions that I want to mount at boot:

/dev/sda1: UUID="DA9056C19056A3B3" LABEL="WinXP" TYPE="ntfs"
/dev/sda6: LABEL="COMMON" UUID="C4DB-C1B0" TYPE="vfat"
/dev/sdb6: LABEL="Data" UUID="f7927995-b098-42be-ada0-987857f5177a" TYPE="ext3"

***STEP 2: Create mount points for your partitions to live in***

Open **Terminal**
Type **sudo mkdir /media/Windows**
Type **sudo mkdir /media/Windows/C**
Type **sudo mkdir /media/Windows/D**
Type **sudo mkdir /media/Data**

***STEP 3: Add lines to /etc/fstab/ to have these partitions mount at boot:***

/dev/sda1 /media/Windows/C      ntfs    defaults,nls=utf8,umask=007,uid=1000,gid=46    0    0
/dev/sda6 /media/Windows/D      vfat    utf8,umask=007,uid=1000,gid=46 0       2
/dev/sdb6 /media/Data     ext3    defaults,noatime 0 2

The last one will mount a linux formatted partition with owner = root and with read / write permissions to root only so that will have to be adjusted after mounting. For example:

Open **Terminal**
Type **sudo chown -R morbius /media/Data**
This will change ownership from root to morbius.

***Step 4: Mount them*** ***by executing the new fstab***

Open **Terminal**
Type [B]sudo mount -a

[/B]There are a great number of different options you can use with these fstab entries depending on your particular needs. Some are only applicable to specific filesystems, but for the most part this is a good starting point. In fact the templates you see in step 3 are what happens when you allow Ubuntu to set up these non-system partitions when choosing the manual partitioning option during an install.

---

### Post by daimaru on 2010-04-02
In Gnome I use mountmanager to permanently mount partitions. Maybe you can use it in KDE too. 

```

sudo apt-get install mountmanager

```
Then mount all your partitions once ( typing in the password each time ) 
go to (in gnome) System->Administration->MountManager

Check to see that all partitions are mounted correctly ( you can choose your own folders if you dont want them to be mounted to /media/b1948725r43852938457 or something like that, by creating a folder sudo mkdir foldername in /media )

But if you just want your partitions to be mounted next time on boot, hit the "Apply button" in the main menu "Partition" ..

Done never need to enter password again.

---

