---
title: "Mount /Film Failed to load"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by Tabu.it on 2011-07-05
Hi, 

I have Ubuntu 10.04 LTS with 2Hd in software Raid 1 and 3hd in a LVM partition (with 2 partition /Download /Films )

This is my fstab config

> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=3bbb8ba4-76b7-4ff2-9d95-a090b16d7825 /               ext4    errors=remount-ro 0       1
# swap was on /dev/md1 during installation
UUID=79afabe2-3f52-4ddd-a365-e4bcbebfe996 none            swap    sw              0       0

##LVM Partition

/dev/FileServer/Films 	/media/Films	ext4	rw,noatime 0 0
/dev/FileServer/Downloads	/media/Downloads	ext4	rw,noatime 0 0	


Each time i boot up ubuntu  require to skip mounting /Films to boot (or to use the recovery console)

DiskUtility show me that the 2gb Hd in the LVM partition have some badsectors.

I have no idea how to fix it(is it hardware problem or os?)

---

### Post by seawolf167 on 2011-07-05
To run a disk check, you can run this

```
sudo fsk -t ext4 -V /dev/FileServer/Film -y
```

---

### Post by Tabu.it on 2011-07-05
OutPut

> 
sudo fsck -t ext4 -V /dev/FileServer/Film -y
fsck from util-linux-ng 2.17.2
[/sbin/fsck.ext4 (1) -- /dev/FileServer/Film] fsck.ext4 -y /dev/FileServer/Film 
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: No such file or directory while trying to open /dev/FileServer/Film

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>



---

### Post by jtarin on 2011-07-05
Try converting "/dev/FileServer/Films /media/Films ext4 rw,noatime 0 0" 
by using [UUID]("https://help.ubuntu.com/community/UsingUUID") rather than designating a /dev.

There is no such designation as /dev/FileServer.....this is not a disk designation.

---

### Post by seawolf167 on 2011-07-05
> **jtarin said:**
> Try converting "/dev/FileServer/Films /media/Films ext4 rw,noatime 0 0" 
by using [UUID]("https://help.ubuntu.com/community/UsingUUID") rather than designating a /dev.

There is no such designation as /dev/FileServer.....this is not a disk designation.

Thanks - I should have caught this, must be tired!

If you type 

```
sudo blkid
```

you can see the UUID's of the partitions, then simply edit /etc/fstab and change that /dev/FileSystem/Film entry

make sure you have the mount point created

```
sudo mkdir /media/Films
```

open /etc/fstab for editing

```
gksu gedit /etc/fstab
```

change the appropriate line, save and exit

---

### Post by Tabu.it on 2011-07-05
> **jtarin said:**
> Try converting "/dev/FileServer/Films /media/Films ext4 rw,noatime 0 0" 
by using [UUID]("https://help.ubuntu.com/community/UsingUUID") rather than designating a /dev.

There is no such designation as /dev/FileServer.....this is not a disk designation.

sudo fsk -t ext4 -V /dev/FileServer/Film -y

Change into sudo fsck -t ext4 -V /dev/FileServer/Films -y

and now is checking

---

### Post by jtarin on 2011-07-05
> **Tabu.it said:**
> sudo fsk -t ext4 -V /dev/FileServer/Film -y

Change into sudo fsck -t ext4 -V /dev/FileServer/Films -y

and now is checkingWRONG!!! Convert the line in /etc/fstab **_to use a UUID number_** by consulting the link I gave. My instructions have nothing to do with filesystem checks. It's about mounting the partition/drive in question.

---

### Post by Tabu.it on 2011-07-05
> **jtarin said:**
> WRONG!!! Convert the line in /etc/fstab **_to use a UUID number_** by consulting the link I gave. My instructions have nothing to do with filesystem checks. It's about mounting the partition/drive in question.

I have this output

tech@Ubuntu:~$ sudo blkid
/dev/sda1: UUID="GJwWeq-r8DD-E67a-Oi7A-gnP1-nvJN-6SwmsD" TYPE="LVM2_member" 
/dev/sdc1: UUID="a305442f-c20d-24ed-ed35-83f8e3193145" TYPE="linux_raid_member" 
/dev/sdc5: UUID="c69e2b4a-21b7-4cda-998c-473424a4f899" TYPE="swap" 
/dev/sdb1: UUID="a305442f-c20d-24ed-ed35-83f8e3193145" TYPE="linux_raid_member" 
/dev/sdb5: UUID="b19e08fb-602e-6304-b4fe-1a131c812286" TYPE="linux_raid_member" 
/dev/sdd1: UUID="lOLqXh-BR1N-toSB-UMxw-xDBD-fa4a-tfzqR1" TYPE="LVM2_member" 
/dev/md1: UUID="79afabe2-3f52-4ddd-a365-e4bcbebfe996" TYPE="swap" 
/dev/md0: UUID="3bbb8ba4-76b7-4ff2-9d95-a090b16d7825" TYPE="ext4" 
/dev/mapper/FileServer-Downloads: UUID="82b37821-c6f5-4529-8f8e-a5a0f1dd375f" TYPE="ext4"

---

### Post by Tabu.it on 2011-07-05
I reboot, same error but this time.

> 
tech@Ubuntu:~$ sudo blkid
/dev/sda1: UUID="a305442f-c20d-24ed-ed35-83f8e3193145" TYPE="linux_raid_member" 
/dev/sda5: UUID="b19e08fb-602e-6304-b4fe-1a131c812286" TYPE="linux_raid_member" 
/dev/sdb1: UUID="a305442f-c20d-24ed-ed35-83f8e3193145" TYPE="linux_raid_member" 
/dev/sdb5: UUID="c69e2b4a-21b7-4cda-998c-473424a4f899" TYPE="swap" 
/dev/sdc1: UUID="GJwWeq-r8DD-E67a-Oi7A-gnP1-nvJN-6SwmsD" TYPE="LVM2_member" 
/dev/sde1: UUID="DC4JRg-Nq0i-Ks6H-3ZlJ-h8XE-rJcK-zWFJXd" TYPE="LVM2_member" 
/dev/sdd1: UUID="lOLqXh-BR1N-toSB-UMxw-xDBD-fa4a-tfzqR1" TYPE="LVM2_member" 
/dev/md1: UUID="79afabe2-3f52-4ddd-a365-e4bcbebfe996" TYPE="swap" 
/dev/md0: UUID="3bbb8ba4-76b7-4ff2-9d95-a090b16d7825" TYPE="ext4" 
/dev/mapper/FileServer-Films: UUID="85bcedad-ed76-4bc6-83af-100cc6144c8e" TYPE="ext4" 
/dev/mapper/FileServer-Downloads: UUID="82b37821-c6f5-4529-8f8e-a5a0f1dd375f" TYPE="ext4" 


Than i do

> 

sudo mount UUID="85bcedad-ed76-4bc6-83af-100cc6144c8e" /media/Films



and the result is 

> 

mount: wrong fs type, bad option, bad superblock on /dev/mapper/FileServer-Films,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



---

### Post by jtarin on 2011-07-05
Your to place that information in your /etc/fstab so it will mount at boot....not to run from terminal as you did.You also need to comment the lines in /etc/fstab so they don't run also.

```
From this:
##LVM Partition

/dev/FileServer/Films /media/Films ext4 rw,noatime 0 0
/dev/FileServer/Downloads /media/Downloads ext4 rw,noatime 0 0 
```
```
To this:
##LVM Partition

#/dev/FileServer/Films /media/Films ext4 rw,noatime 0 0
#/dev/FileServer/Downloads /media/Downloads ext4 rw,noatime 0 0 
```

---

### Post by Tabu.it on 2011-07-05
> **jtarin said:**
> Your to place that information in your /etc/fstab so it will mount at boot....not to run from terminal as you did.You also need to comment the lines in /etc/fstab so they don't run also.

```
From this:
##LVM Partition

/dev/FileServer/Films /media/Films ext4 rw,noatime 0 0
/dev/FileServer/Downloads /media/Downloads ext4 rw,noatime 0 0 
```
```
To this:
##LVM Partition

#/dev/FileServer/Films /media/Films ext4 rw,noatime 0 0
#/dev/FileServer/Downloads /media/Downloads ext4 rw,noatime 0 0 
```

Is it right?

##LVM Partition

##/dev/FileServer/Films         /media/Films    ext4    rw,noatime 0 0
UUID="85bcedad-ed76-4bc6-83af-100cc6144c8e" /media/Films

##/dev/FileServer/Downloads     /media/Downloads        ext4    rw,noatime 0 0
UUID="82b37821-c6f5-4529-8f8e-a5a0f1dd375f" /media/Downloads

Thank you

---

### Post by Tabu.it on 2011-07-05
My fstab now

> 


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=3bbb8ba4-76b7-4ff2-9d95-a090b16d7825 /               ext4    errors=remount-ro 0       1
# swap was on /dev/md1 during installation
UUID=79afabe2-3f52-4ddd-a365-e4bcbebfe996 none            swap    sw              0       0

##LVM Partition

##/dev/FileServer/Films         /media/Films    ext4    rw,noatime 0 0
UUID="85bcedad-ed76-4bc6-83af-100cc6144c8e" /media/Films ext4    rw,noatime 0 0

##/dev/FileServer/Downloads     /media/Downloads        ext4    rw,noatime 0 0
UUID="82b37821-c6f5-4529-8f8e-a5a0f1dd375f" /media/Downloads ext4    rw,noatime 0 0



Same problem at boot

---

### Post by jtarin on 2011-07-05
> **Tabu.it said:**
> My fstab now



Same problem at boot
Maybe try to reconfigure the part "ext4 rw,noatime 0 0".
Here's a [link]("https://help.ubuntu.com/community/Fstab") to sort it out according to what you want and need.
I can't comment beyond this.Sorry, it sounds as if your filesystem is whacked. Have you successfully mounted it before?

---

### Post by Tabu.it on 2011-07-06
> **jtarin said:**
> Maybe try to reconfigure the part "ext4 rw,noatime 0 0".
Here's a [link]("https://help.ubuntu.com/community/Fstab") to sort it out according to what you want and need.
I can't comment beyond this.Sorry, it sounds as if your filesystem is whacked. Have you successfully mounted it before?


Was mounted since 3/2011 without problems. Yesterday i reboot the server and the problem came out.

---

### Post by Zill on 2011-07-06
Tabu.it:  Have you tried using the UUID in /etc/fstab *without* the quotation marks? eg.
```
UUID=85bcedad-ed76-4bc6-83af-100cc6144c8e /media/Films ext4 rw,noatime 0 0
UUID=82b37821-c6f5-4529-8f8e-a5a0f1dd375f /media/Downloads ext4 rw,noatime 0 0
```

---

### Post by Tabu.it on 2011-07-06
> **Zill said:**
> Tabu.it:  Have you tried using the UUID in /etc/fstab *without* the quotation marks? eg.
```
UUID=85bcedad-ed76-4bc6-83af-100cc6144c8e /media/Films ext4 rw,noatime 0 0
UUID=82b37821-c6f5-4529-8f8e-a5a0f1dd375f /media/Downloads ext4 rw,noatime 0 0
```


I'll try it after fsck, but i think the problem is the HD 

[[IMG]http://img268.imageshack.us/img268/1239/linuxaa.jpg[/IMG]](http://imageshack.us/photo/my-images/268/linuxaa.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

EDIT: No change after /etc/fstab edit
EDIT2: The number of badsectors is growing 

Is there some way to backup the /media/Films Partition?

---

