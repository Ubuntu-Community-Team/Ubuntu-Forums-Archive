---
title: "Please help with permissions on extra hard drives"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by ianb72 on 2009-01-26
I have run my hard drive down to only just over 200Kb left so i have found 4 old 20Gb IDE drives that I've added 2 at a time, I have formatted these in ext3 format using GParted.

Now could someone please please tell me in easy steps how I can change the read/write permissions of these drives so I can copy over loads of files to free up 80Gb of my main Sata drive.

Here is the list of my drives that are presently in my system

[HTML] ian@ian-desktop:~$ sudo fdisk -l

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe41fe41

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2434    19551073+  83  Linux

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xca64ca64

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       38792    19551136+  83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a840b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30047   241352496   83  Linux
/dev/sda2           30048       30401     2843505    5  Extended
/dev/sda5           30048       30401     2843473+  82  Linux swap / Solaris
ian@ian-desktop:~$ [/HTML]

Thank you for any help anyone can give me, cos at the moment I cant even get any emails due to lack of space on my 250Gb main drive!!

Ian

---

### Post by whoop on 2009-01-26
Wait for other to confirm this :-)

Mount /dev/hdc1 somewhere using fstab, then

```

sudo chown ian:ian /mountpoint
sudo chmod 700 /mountpoint

```

---

### Post by bodhi.zazen on 2009-01-26
you can copy files as root

either sudo cp ...

or use gksu nautilus

You set permissions at the time of mounting the partition, but it is different with windows and linux.

See [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Coreigh on 2009-01-26
first mount the disks. Make a mount point:
```
sudo mkdir /mnt/hdc
sudo mkdir /mnt/hdd
```

This makes a place to mount the disks. I named them after what they are, but you can call then whatever you want to. Next, mount them:
```
sudo mount /dev/hdc1 /mnt/hdc
sudo mount /dev/hdd1 /mnt/hdd
```

This mounts the disks to the file system. At this point when you change directories to /mnt/hdd you won't be simply entering a folder named hdd but changing on the the disk hdd1. Also you should have permission to create folders and copy files.

Finally make the mounts persistent by editing the fstab. Open the fstab as root;
```
sudo gedit /etc/fstab
```
you will see something similar to this:
> # /etc/fstab: static file system information.
#
#<file system>					<mount point>	<type>			<options>				<dump>	<pass>
proc						/proc			proc		defaults				0       0

# /dev/sda2
UUID=0cb89576-903f-42b4-be33-bef7d90910c4	/			ext3		defaults,errors=remount-ro		0       1

# /dev/sda1
UUID=80246E6D246E65DE				/windows		ntfs		defaults,umask=007,gid=46		0       1

# /dev/sda5
UUID=83782710-04c0-404b-8df4-10ef019e0270	none			swap		sw					0       0

/dev/scd0					/media/cdrom0		udf,iso9660	user,noauto,exec			0       0
/dev/fd0					/media/floppy0		auto		rw,user,noauto,exec			0       0


You will wan to add entries for hdc and hdd, like this:
> # /dev/hdc1
/dev/hdc1	/mnt/hdc			ext3		defaults,errors=remount-ro		0       1
# /dev/hdd1
/dev/hdc1	/mnt/hdd			ext3		defaults,errors=remount-ro		0       1


**[COLOR="Red"]Now, DON'T just copy what I typed![/COLOR]** Make sure everything is right. You have to use the correct disk and mount point for your setup, don't trust that I typed it right. Also there is a strong argument to use UUIDs instead of /dev 's but that is another article and easy enough to look up.

Finally I have to point out that I know everyone is tight on cash but it would be a lot less headaches to go get a single big disk and not mess with all this extra mounting.

---

### Post by mkvnmtr on 2009-01-26
I have struggled for a couple of days to get my esternals to mount on 3 Ubuntu distros to back up all three an one drive. Finally I downloaded Storage Device Manager to all of the systems. Then I stick the drive in. I go to the device manager and accept the defaults. It gives you a mount point and will mount when you click on mount. It will unmount when you want to disconect. Every time I tried to use it to change permissions I had problems. Then to get the permissions how i wanted I went to the terminal and typed

{sudo chmod 777 -R /mount point}    
The mount point was something like  /media/sdb2  whatever the device manager said. I did this on every os. I think the problem I had was related to what file system the partitions were formated to. I wound up using unjourneled hfsplus because  I have a Mac in play also. Now all five externals work on all four systems. Before I got the device Manager changing ownership or permissions would just change back to read only with root the owner. Quite a trail but it is all working like I want now.

---

### Post by bodhi.zazen on 2009-01-26
:lolflag:

chown and chmod does not work on FAT or NTFS partitions.

We do not know what type of partition we are working with (there is a bug in Ubuntu that lists FAT / NTFS partitions as "Linux" in fdisk)

**root@ufbt:~#fdisk -l**
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         200     1606468+  83  **Linux**
/dev/sdb2             201         401     1614532+  83  **Linux**
/dev/sdb3             402         652     2016157+   5  Extended
/dev/sdb5             402         652     2016126   83  **Linux**

**root@ufbt:~#blkid**
/dev/sdb1: UUID="727e3306-bbcc-4849-b801-3e052b3622a0" TYPE="**ext3**"
/dev/sdb2: UUID="2C62877707754728" TYPE="**ntfs**"
/dev/sdb5: UUID="E8D1-531A" TYPE="**vfat**"

---

