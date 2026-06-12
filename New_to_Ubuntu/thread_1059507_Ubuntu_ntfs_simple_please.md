---
title: "Ubuntu ntfs simple please"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by ubdude on 2009-02-03
Hi all.

just joined the community. Fed up of corporate windows. Vista was slow and making fire fox crash and utorrent stop responding. So far has been gd. got thuderbird installed and skype. now i want to read ntfs. So far i have found nothing that has given SIMPLE EASY TO FOLLOW instructions to geting ntfs drives working on ubuntu. I have ubuntu 8.10 installed on primary 40Gb HD. i then have a 200gb ide and a 70gb sata i want to see and read write files (old data stored on eg films music photos.

PLEASE CAN SOMEONE GIVE SIMPLE EASY TO FOLLOW INSTRUCTIONS TO GET NTFS DRIVES TO BE SEEN IN MY NEW UBUNTU INSTALL 8.10.

THANK YOU:(

---

### Post by jerome1232 on 2009-02-03
NTFS is read/writable out of the box with ubuntu.

Click Places->Click on the partition it should get mounted

Also ntfs-config is a nice gui for getting ntfs drives auto-mounted during the boot process, just pop open synaptic (System-Administration-Synaptic Package Manager) search for ntfs-config and mark it for installation.

---

### Post by ubdude on 2009-02-03
thanx but dont work. you are not privileged to mount this volume is what i get

---

### Post by jerome1232 on 2009-02-03
> **ubdude said:**
> thanx but dont work. you are not privileged to mount this volume is what i get

Did you try using ntfs-config?

---

### Post by sandyd on 2009-02-03
do this...

yes, people don't blame me for this, i'm being teribly unsafe.....:o

type this in terminal
```
sudo nautilus
```

then try mounting it again in the window that just appeared

---

### Post by ubdude on 2009-02-03
NTFS configuration tool does not help if that's what you mean. I am a complete noob to ubuntu mate. Any elaboration on your answers will help. I don't want to loose any of my data on the 70 and 200 GB drives. All I want to do is see them and access the data and read/write files like normal day to day activity. I previously had vista on the 40gb drive that now has solely ubuntu 8.10 

CHEERS

---

### Post by Crafty Kisses on 2009-02-03
Do as carlee suggested. Press Alt+F2 and type the following:
```
gksudo nautilus
```
Then see if you can mount the drive, and see the files.

---

### Post by ubdude on 2009-02-03
dont have a clue what your on about. did that and jus opens a new window with desktop shortcut in it. i want to be able to go to computer click on drives and view what is on them and read write data like everyday activity

---

### Post by jbehl on 2009-02-03
> **ubdude said:**
> dont have a clue what your on about. did that and jus opens a new window with desktop shortcut in it. i want to be able to go to computer click on drives and view what is on them and read write data like everyday activity

I'm in the exact same boat. I'm looking to be able to access my old storage drive as well.

---

### Post by ubdude on 2009-02-03
Im gonna put the kettle on. This could be a long one. Does anyone know what im on about? 

I know how carry out simple instructions, provided they are simple.

:D

---

### Post by jerome1232 on 2009-02-03
Can you post the output of these commands please, I can show you how to manually edit your fstab and get everything going, but it's easiest going with the command line. To open a terminal Click Applications-Accessories-Terminal

```
sudo fdisk -l
sudo blkid
mount
```

fdisk -l list current partitions and disks
blikd print there uuid's (needed for editing your fstab)
mount will print current mount points, just to make sure none of them are mounted and etc..

---

### Post by jbehl on 2009-02-03
> **jerome1232 said:**
> Can you post the output of these commands please, I can show you how to manually edit your fstab and get everything going, but it's easiest going with the command line. To open a terminal Click Applications-Accessories-Terminal

```
sudo fdisk -l
sudo blkid
mount
```

fdisk -l list current partitions and disks
blikd print there uuid's (needed for editing your fstab)
mount will print current mount points, just to make sure none of them are mounted and etc..

Not to hijack ubdude's thread, but...
Here's mine:

james@Behl-Desktop:~$ sudo fdisk -l
[sudo] password for james: 

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4310    34620043+  83  Linux
/dev/sda2            4311        4500     1526175    5  Extended
/dev/sda5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10cb8b7d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?           1       19457   156288321    7  HPFS/NTFS
james@Behl-Desktop:~$ 
james@Behl-Desktop:~$ sudo blkid
/dev/sda1: UUID="424761ac-3204-4113-b80b-41f36b40ac8a" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="58f7bb1a-5b16-41e6-9338-503f86aa7175" 
james@Behl-Desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)

---

### Post by ubdude on 2009-02-03
and mee lol

Disk /dev/sdb: 80.0 GB, 80000000000 bytes

255 heads, 63 sectors/track, 9726 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00026da4



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1        9726    78124063+   7  HPFS/NTFS



Disk /dev/sdc: 203.9 GB, 203928109056 bytes

255 heads, 63 sectors/track, 24792 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xa0a4cb35



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1   *           1       24792   199141708+   7  HPFS/NTFS



Disk /dev/sdd: 2043 MB, 2043674624 bytes

255 heads, 63 sectors/track, 248 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x04030201



   Device Boot      Start         End      Blocks   Id  System

/dev/sdd1   *           1         247     1983996    6  FAT16

dude@dude-desktop:~$ 



dude@dude-desktop:~$ sudo blkid

[sudo] password for dude: 

/dev/sda1: UUID="158d2978-53d7-45d1-b616-71cbee7d46d3" TYPE="ext3" 

/dev/sda5: TYPE="swap" UUID="8c7a4154-b266-4a7d-bbe4-ade6d97ffc86" 

/dev/sdb1: UUID="8C505756505745DC" LABEL="OLD" TYPE="ntfs" 

/dev/sdc1: UUID="86CC8BA5CC8B8DDD" LABEL="200G" TYPE="ntfs" 

/dev/sdd1: SEC_TYPE="msdos" UUID="1C0A-BEDF" TYPE="vfat" 

dude@dude-desktop:~$ 






255 heads, 63 sectors/track, 248 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x04030201



   Device Boot      Start         End      Blocks   Id  System

/dev/sdd1   *           1         247     1983996    6  FAT16

dude@dude-desktop:~$ mount

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)

tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)

/proc on /proc type proc (rw,noexec,nosuid,nodev)

sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)

varrun on /var/run type tmpfs (rw,nosuid,mode=0755)

varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)

udev on /dev type tmpfs (rw,mode=0755)

tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)

devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)

fusectl on /sys/fs/fuse/connections type fusectl (rw)

lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)

securityfs on /sys/kernel/security type securityfs (rw)

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

gvfs-fuse-daemon on /home/dude/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dude)

dude@dude-desktop:~$ 


cheers

---

### Post by jerome1232 on 2009-02-03
It helps if your wrap all of the output in code tags, basically just put the output between these -->[noparse]```
 output of command here
```[/noparse]

> **jbehl said:**
> Not to hijack ubdude's thread, but...
Here's mine:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10cb8b7d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?           1       19457   156288321    7  HPFS/NTFS
james@Behl-Desktop:~$ 
james@Behl-Desktop:~$ sudo blkid
/dev/sda1: UUID="424761ac-3204-4113-b80b-41f36b40ac8a" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="58f7bb1a-5b16-41e6-9338-503f86aa7175" 


Ooops I hope nothing is wrong with your partition, let's try manually mounting and see if there are errors.

```
sudo -i
mkdir /media/ntfsdisk
mount /dev/sdb1 /media/ntfsdisk -o umask=000
exit
```

If there's an error post it, if it works you should have an icon for that disk, try and browse it, if all is well we can go ahead and setup fstab.

let me know if there's any errors from that, if so post them, it helps readablity to put the output in code tags



> **ubdude said:**
> and mee lol

   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1        9726    78124063+   7  HPFS/NTFS


   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1   *           1       24792   199141708+   7  HPFS/NTFS

   Device Boot      Start         End      Blocks   Id  System

/dev/sdd1   *           1         247     1983996    6  FAT16


/dev/sdb1: UUID="8C505756505745DC" LABEL="OLD" TYPE="ntfs" 

/dev/sdc1: UUID="86CC8BA5CC8B8DDD" LABEL="200G" TYPE="ntfs" 

/dev/sdd1: SEC_TYPE="msdos" UUID="1C0A-BEDF" TYPE="vfat" 


cheers


```
gksu gedit /etc/fstab
```

Copy and past this stuff in
```

### copy and paste this below ###
# /dev/sdb1, old
UUID=8C505756505745DC /media/old ntfs-3g umask=000 0 0
# /dev/sdc1, 200G
UUID=86CC8BA5CC8B8DDD /media/storage ntfs-3g umask=000 00
# /dev/sdc1, fatdrive
UUID=1C0A-BEDF /media/fatdrive vfat umask=000 0 0

```

Save the file, make those directories then mount it.

```
sudo -i
mkdir /media/old; mkdir /media/storage; mkdir /media/fatdrive
mount -a
exit
```

It should all be working.

---

### Post by jbehl on 2009-02-03
> **jerome1232 said:**
> It helps if your wrap all of the output in code tags, basically just put the output between these -->[noparse]```
 output of command here
```[/noparse]



Ooops I hope nothing is wrong with your partition, let's try manually mounting and see if there are errors.

```
sudo -i
mkdir /media/ntfsdisk
mount /dev/sdb1 /media/ntfsdsik -o umask=000
exit
```

If there's an error post it, if it works you should have an icon for that disk, try and browse it, if all is well we can go ahead and setup fstab.

let me know if there's any errors from that, if so post them, it helps readablity to put the output in code tags


```

james@Behl-Desktop:~$ sudo -i
[sudo] password for james: 
root@Behl-Desktop:~# mkdir /media/ntfsdisk
root@Behl-Desktop:~# mount /dev/sdb1 /media/ntfsdisk -o unmask=000
mount: special device /dev/sdb1 does not exist
root@Behl-Desktop:~# 

```

I got the above errors. 

This is beyond me. My USB drives I used on the XP machine work in Ubuntu perfectly. This one was fine as well when XP was installed. Unless it went bad during the Ubuntu install, nothing has changed.

BTW-Thanks for all of the help. I hope we can get it up and running.

---

### Post by jerome1232 on 2009-02-03
> 
Code:

james@Behl-Desktop:~$ sudo -i
[sudo] password for james: 
root@Behl-Desktop:~# mkdir /media/ntfsdisk
root@Behl-Desktop:~# mount /dev/sdb1 /media/ntfsdisk -o unmask=000
mount: special device /dev/sdb1 does not exist
root@Behl-Desktop:~#

I got the above errors.

This is beyond me. My USB drives I used on the XP machine work in Ubuntu perfectly. This one was fine as well when XP was installed. Unless it went bad during the Ubuntu install, nothing has changed.

BTW-Thanks for all of the help. I hope we can get it up and running. 

Yeah I'm not sure man, I'd start a new thread describing the problem your having, put the "fdisk -l" output and the error from that mount command in your first post, I'm sure someone that knows more about working with partitions than I will be able to help you.

Maybe even link this thread so that people can see what I've told you so far as well.

I think your partition table may have been corrupted somehow. *If* that's the case testdisk should be able to restore the partition table. But unfortunately I can't be of help in figuring this out for you.

---

### Post by Andy06 on 2009-02-03
Hi,

I don't think there is anything wrong with your partition table or with you disks. Despite 8.10 having out of box support for NTFS, actually mounting and using them is a bit of a pain which gets worse when you try and "manage" them with a program. I have had the same issues as you on multiple computers.

What you need to do is goto System>Administration>Users and Groups, then click on your user name and select unlock, enter your password and select account privileges in the new thing that comes up, here make sure to select "access external storage" and "mount user space filesystems FUSE". While you're at it, tick other stuff that you might need.

Try now, you should be able to mount. If not, install Disk Manager from add/remove or synaptic package manager, its like NTFS config, but I think its way better and definitely has more features. The GUI is pretty simple and self explanatory.

Disk manager will appear in System>Administration>Disk manager.

In 1st tab (General), select detect devices on start up and enable write support, then configure you devices. There is an auto configure option too.

Let me know how it works out.


Also could someone explain to me why NTFS config is the most recommended tool? I tried using it but it replicates some of the functionality already there in 8.10 and doesn't do much. Don't NTFS config and Disk Manager do exactly the same things?

Thanks

---

### Post by Victormd on 2009-02-03
You might want to manually set fstab to automount your NTFS partitions... check the link on my signature...

---

### Post by jerome1232 on 2009-02-03
> **Andy06 said:**
> 
Also could someone explain to me why NTFS config is the most recommended tool? I tried using it but it replicates some of the functionality already there in 8.10 and doesn't do much. Don't NTFS config and Disk Manager do exactly the same things?

Thanks

I've never used those gui programs I find they make everything much more difficult than it should be. I just say ntfs-config because I've heard it's good and I've seen people successfully use it. If disk manager is better maybe I should start recommending that vs ntfs-config.

There is definitly something wrong there read the output from fdisk and the mount command. Although it won't hurt to try these other methods so go ahead, if it works then gratz ;)

```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10cb8b7d
[COLOR="Red"]
This doesn't look like a partition table
Probably you selected the wrong device.[/COLOR]

Device Boot Start End Blocks Id System
/dev/sdb1 ? 1 19457 156288321 7 HPFS/NTFS
```

```
mount /dev/sdb1 /media/ntfsdisk -o unmask=000
[COLOR="Red"]mount: special device /dev/sdb1 does not exist[/COLOR]
```

fdisk can't find a partition table (it's apparently guessing what's there) and the device sdb1 isn't getting created by the system. If the device doesn't exist in /dev then you can't mount it.

---

### Post by jbehl on 2009-02-03
> **jerome1232 said:**
> I've never used those gui programs I find they make everything much more difficult than it should be. I just say ntfs-config because I've heard it's good and I've seen people successfully use it. If disk manager is better maybe I should start recommending that vs ntfs-config.

There is definitly something wrong there read the output from fdisk and the mount command. Although it won't hurt to try these other methods so go ahead, if it works then gratz ;)

```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10cb8b7d
[COLOR="Red"]
This doesn't look like a partition table
Probably you selected the wrong device.[/COLOR]

Device Boot Start End Blocks Id System
/dev/sdb1 ? 1 19457 156288321 7 HPFS/NTFS
```

```
mount /dev/sdb1 /media/ntfsdisk -o unmask=000
[COLOR="Red"]mount: special device /dev/sdb1 does not exist[/COLOR]
```

fdisk can't find a partition table (it's apparently guessing what's there) and the device sdb1 isn't getting created by the system. If the device doesn't exist in /dev then you can't mount it.

I used testdisk and got the partition back up. I got the following from the orginal code set:
```

james@Behl-Desktop:~$ sudo fdisk -l
[sudo] password for james: 

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4310    34620043+  83  Linux
/dev/sda2            4311        4500     1526175    5  Extended
/dev/sda5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10cb8b7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS
james@Behl-Desktop:~$ sudo blkid
/dev/sda1: UUID="424761ac-3204-4113-b80b-41f36b40ac8a" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="58f7bb1a-5b16-41e6-9338-503f86aa7175" 
/dev/sdb1: UUID="01C412E35FE2ED00" LABEL="Storage 1" TYPE="ntfs" 
james@Behl-Desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)

```

---

### Post by jerome1232 on 2009-02-03
> **jbehl said:**
> I used testdisk and got the partition back up. I got the following from the orginal code set:
```

james@Behl-Desktop:~$ sudo fdisk -l
[sudo] password for james: 

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4310    34620043+  83  Linux
/dev/sda2            4311        4500     1526175    5  Extended
/dev/sda5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10cb8b7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS
james@Behl-Desktop:~$ sudo blkid
/dev/sda1: UUID="424761ac-3204-4113-b80b-41f36b40ac8a" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="58f7bb1a-5b16-41e6-9338-503f86aa7175" 
/dev/sdb1: UUID="01C412E35FE2ED00" LABEL="Storage 1" TYPE="ntfs" 
james@Behl-Desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)

```

Ok glad testdisk got it going, I wonder how that partition table got messed up.

Does blkid give an uuid for /dev/sdb1 now?

```
sudo blkid
```

---

### Post by jbehl on 2009-02-04
> **Andy06 said:**
> Hi,

I don't think there is anything wrong with your partition table or with you disks. Despite 8.10 having out of box support for NTFS, actually mounting and using them is a bit of a pain which gets worse when you try and "manage" them with a program. I have had the same issues as you on multiple computers.

What you need to do is goto System>Administration>Users and Groups, then click on your user name and select unlock, enter your password and select account privileges in the new thing that comes up, here make sure to select "access external storage" and "mount user space filesystems FUSE". While you're at it, tick other stuff that you might need.

Try now, you should be able to mount. If not, install Disk Manager from add/remove or synaptic package manager, its like NTFS config, but I think its way better and definitely has more features. The GUI is pretty simple and self explanatory.

Disk manager will appear in System>Administration>Disk manager.

In 1st tab (General), select detect devices on start up and enable write support, then configure you devices. There is an auto configure option too.

Let me know how it works out.


Also could someone explain to me why NTFS config is the most recommended tool? I tried using it but it replicates some of the functionality already there in 8.10 and doesn't do much. Don't NTFS config and Disk Manager do exactly the same things?

Thanks

Disk manager was the fix. I can see the drive and the files. Thanks for all of the helps guys.

---

### Post by ubdude on 2009-02-04
IN SIMPLE LAYMAN'S TERMS. THE MOST SIMPLEST WAY IS WHAT I WAS AFTER. 

INSTALL DISK MANAGER. 

system/admin/synaptic package manager/(search disk manager and tick and mark for installation.

THEN OPEN DISK MANAGER

system/admin/disk manager

IN DISK MANAGER TICK DRIVES AND TRY MOUNT (did not work for me just yet)

THEN EDIT THE DRIVES AND USE THE NTFS 3G DRIVER.

THEN I FOUND A FORCE MOUNT TICK BOX THAT SEEMED TO DO THE JOB. 

NOW I CAN READ WRITE DATA FROM MY NTFS DRIVES.



I WISH SOME ONE HAD JUST TOLD ME THAT IN THE FIRST PLACE WITHOUT ALL THE JARGON. HENCE THE TITLE OF POST, SIMPLE NTFS.


I HOPE THIS HELPS OTHERS

---

### Post by Andy06 on 2009-02-04
Yeah I always use Disk manager, I dint even have to force or edit driver, just configure on first tab and maybe select auto configure. I dunno why NTFS config is so popular on these forums, maybe a legacy thing since NTFS config did what Ubuntu now does natively but now NTFS config is much less powerful than Disk manager.

Also the things people do to fstab and mountpoint and the lines and lines on code in the terminal to achieve the same goal is just plain scary. They're probably very good and do manually what disk manager does with a GUI.

Unfortunately telling newbies "simple" commands to put into terminal is not good practice IMO coz they never internalise the process, telling them what to do with GUI means they're now good to go every single time.

Hell Disk manager even mounts stuff when windows has had an unclean shut down, that was a pain to do before :)

---

### Post by jbehl on 2009-02-04
> **Andy06 said:**
> 
Hell Disk manager even mounts stuff when windows has had an unclean shut down, that was a pain to do before :)

That was the error message I was getting. The disk had an unclean shutdown.

---

### Post by Andy06 on 2009-05-13
@jbehl,ubdude

Have you guys upgraded to 9.04 yet? I can't find Disk manager anywhere in the repos! Wonder where it went. Pysdm package(Storage device manager) has a resemblance so I'm wondering if that's a new version. However, the GUI and functionality seem completely different.

---

### Post by sathgarcia on 2009-05-13
am a newbie as well, not sure it this will help in 8.10.  Anyway, it works on 8.04 . . .

you might wanna try this . . . apt-get install pysdm :D

---

