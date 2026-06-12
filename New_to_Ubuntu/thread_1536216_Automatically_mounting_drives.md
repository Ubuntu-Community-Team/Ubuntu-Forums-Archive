---
title: "Automatically mounting drives?"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by bthomson100 on 2010-07-21
I have an Acer Aspire 3104 laptop running Ubuntu 10.4 and Windows Vista.

I installed the storage device manager but I think I've somehow screwed up the parameters and now I have to go to a terminal to type "mount /dev/sdb1 on /media/sda1" (or sdc1, sdc3, etc.) in order to be able to access the drives.

My internal hard drive has 2 partitions, C and D. Partition C mounts automatically when I start Ubuntu, but the others don't and I get a message asking if I want to continue without mounting by pressing S.

The other 2 drives are a 250 gb Seagate FreeAgent drive and an 80 gb Iomega backup drive, both connected via USB ports.

How can I get them to mount automatically?

Bob Thomson

---

### Post by Zeike on 2010-07-21
> **bthomson100 said:**
> My internal hard drive has 2 partitions, C and D. Partition C mounts automatically when I start Ubuntu, but the others don't and I get a message asking if I want to continue without mounting by pressing S.

The other 2 drives are a 250 gb Seagate FreeAgent drive and an 80 gb Iomega backup drive, both connected via USB ports.

How can I get them to mount automatically?

Hello!

First, the partitions are not called C and D in Ubuntu.  These are names that Windows sticks on them.

To mount these partitions automatically you can add the necessary lines to the /etc/fstab file.  For some info on this see here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you need help with anything, please ask.

---

### Post by garvinrick4 on 2010-07-21
The USB drives:
Install gconf-editor:

```
sudo apt-get install gconf-editor
```It will be in Applications to System tools to Configuration Editor.
Open and go to Apps to Nautilus to Preferences and to media_automount and make 
sure it is checked.

You are using Wubi I imagine and in Windows install it will be given a letter and in
linux you get a sdax, or sdbx and so on. In partition install if you make a partition in
Fat32 format it will be like sda7 in Ubuntu and something like F: drive in your Windows install.

---

### Post by bthomson100 on 2010-07-21
I installed gconf-editor but it doesn't appear in Applications-System Tools. I ran it from a console and media_automount is checked.

I've also looked at the fstab documentation and at my fstab file.

My fstab file reads (among other things):

/dev/sdb1                     /media/sda1  ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sdc1                     /media/sdc1  vfat  defaults                    0  0  
/dev/sda3                     /media/sda3  ntfs  nls=iso8859-1,ro,umask=000  0  0 

This seems counter intuitive to me as the mount points should have the same names as the devices shouldn't they?

When I do sudo fdisk -l, I get info on sda (3 of them!), sdb (one) and sdc (one)

sda is my internal hard drive with sda1 seeming to be a boot sector, sda2 being what Windows calls drive c and sda3 being what Windows calls drive d. sda2 also seems to be recognized as ACER by Ubuntu and it mounts only if one chooses if from the Places menu in Ubuntu's top toolbar.

sdb1 seems to be my 250 gb Seagate FreeAgent drive

Clicking "Free Agent Drive" in the Ubuntu Places menu generates the message
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/sdc1

sdc1 seems to be my 80 gb Iomega backup HDD

Clicking "IOMEGA_HDD" in the Ubuntu Places menu generates the message
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/sda1

I would think then that the fstab file should read something like this.

# /dev/sda1                   /media/sda1  
# /dev/sda2                   /media/sda2  FAT16 
# /dev/sda3                   /media/sda3  HPFS/NTFS
# /dev/sdb1                   /media/sdb1  HPFS/NTFS
# /dev/sdc1                   /media/sdc1  W95 FAT32

I'm not so sure about the parameters. The file system types above I got from the fdisk command and I have no idea what the other options in the fstab file are or if they are necessary.

Can anyone suggest what I should have in my fstab file given the above information?

Bob Thomson

---

### Post by Zeike on 2010-07-22
> **bthomson100 said:**
> When I do sudo fdisk -l, I get info on sda (3 of them!), sdb (one) and sdc (one)

Can you post the output of 'fdisk -l'?

---

### Post by bthomson100 on 2010-07-22
bobt@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41f009f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1147     9213246   27  Unknown
/dev/sda2   *        1148        7889    54155115    6  FAT16
/dev/sda3            7890       14593    53849880    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 82.3 GB, 82348278272 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b99a425

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10011    80413326    b  W95 FAT32
bobt@ubuntu:~$ ^C

---

### Post by Morbius1 on 2010-07-22
I generally prefer to work with the output of the following command to see what partitions I have and how they are formatted:
```
sudo blkid -c /dev/null
```It will list your partitions by UUID, LABEL, and /dev/sdxy and tell you how it's formatted.

Anyway lets see if we can fix the one internal drive:
> /dev/sda3 /media/sda3 ntfs nls=iso8859-1,ro,umask=000 0 0 ro = read only
umask=000 gives read write access to everyone
There's no telling who wins that contest.

First I would create a mount point for the sda3 to live in with a name that doesn't confuse me:
```
sudo mkdir /media/WinD
```Then change the fstab line above to read like this:
> /dev/sda3 /media/WinD ntfs defaults,nls=utf8,umask=000 0 0The umask=000 really isn't necessary because it's in the defaults but I like to have it there anyway so there never any doubt about how I set this up.

---

### Post by bodhi.zazen on 2010-07-22
> **Morbius1 said:**
> The umask=000 really isn't necessary because it's in the defaults but I like to have it there anyway so there never any doubt about how I set this up.

You might enjoy dmask and fmask . These are similar to umask, but set permissions on directories and files separately, thus not all your files are executable =)

---

### Post by Morbius1 on 2010-07-22
> **bodhi.zazen said:**
> You might enjoy dmask and fmask . These are similar to umask, but set permissions on directories and files separately, thus not all your files are executable =)
You are absolutely right. And if I was really doing my job right I would mention those. But mostly in this forum I'm in a mad rush just to keep people from going to the dark side and using some GUI to do this :)

---

### Post by bodhi.zazen on 2010-07-22
> **Morbius1 said:**
> You are absolutely right. And if I was really doing my job right I would mention those. But mostly in this forum I'm in a mad rush just to keep people from going to the dark side and using some GUI to do this :)

Nice 

:lolflag:

---

### Post by bthomson100 on 2010-07-23
[QUOTE=Morbius1;9624025]I generally prefer to work with the output of the following command to see what partitions I have and how they are formatted:
```
sudo blkid -c /dev/null
```

Ok. This output was as follows:
root@ubuntu:~# sudo blkid -c /dev/null
/dev/loop0: UUID="168c9f8b-21e9-4b86-a9e1-e50e6dfaa0fb" TYPE="ext4" 
/dev/sda1: LABEL="PQSERVICE" UUID="8280B59816D9B5D2" TYPE="ntfs" 
/dev/sda2: LABEL="ACER" UUID="76B81A5DB81A1C65" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="FA7411D27411930D" TYPE="ntfs" 
/dev/sdb1: LABEL="IOMEGA_HDD" UUID="6BFB-3DFE" TYPE="vfat" 
/dev/sdc1: LABEL="FreeAgent Drive" UUID="D0D03710D036FC72" TYPE="ntfs" 
root@ubuntu:~# 

I've created the directory /media/WinD and the line as you suggested in fstab.

Now what? Do I have to restart to have it take effect?

Bob

---

### Post by Morbius1 on 2010-07-23
Just open up a terminal and type:
```
sudo mount -a
```It will mount the new entry is fstab - no need to reboot.

The mount command may give you errors if you did a typo or if the entry isn't correct. If it does post back with that error message.

---

### Post by bthomson100 on 2010-07-23
I did sudo mount -a and this is the error message I got.

root@ubuntu:~# sudo mount -a
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

fuse: mount failed: Device or resource busy
root@ubuntu:~#

---

### Post by Morbius1 on 2010-07-23
Your answer is here:
> Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used?sdb1 isn't ntfs it's vfat ( FAT32 ):
>  /dev/sdb1: LABEL="IOMEGA_HDD" UUID="6BFB-3DFE" TYPE="vfat" Why not post your fstab:
```
cat /etc/fstab
```

---

### Post by bodhi.zazen on 2010-07-23
> **bthomson100 said:**
> I did sudo mount -a and this is the error message I got.

root@ubuntu:~# sudo mount -a
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

fuse: mount failed: Device or resource busy
root@ubuntu:~#

sdb1 is a fat partition

so, in fstab, change

> /dev/sdb1                     /media/sda1  ntfs  nls=iso8859-1,ro,umask=000  0 to 

```
/dev/sdb1                     /media/sda1 vfat umask=000  0  0
```

Your ro option conflicts with umast=000. If you want ro, use a different umask value ;)

For the options with vfat, see man mount.

---

### Post by Morbius1 on 2010-07-23
I think we have a more fundamental problem here which might explain the sdxy mix up. These are both external drives I think:
> /dev/sdb1: LABEL="IOMEGA_HDD" UUID="6BFB-3DFE" TYPE="vfat" 
/dev/sdc1: LABEL="FreeAgent Drive" UUID="D0D03710D036FC72" TYPE="ntfs" At this very moment they are at sdb1 and sdc1 but they may not be tomorrow. If the IOMEGA is removed, for example, then the next time you boot the FreeAgent will be sdb1. Your fstab won't work again.

I think we need to use either LABEL's or UUID's to specify these devices in fstab.

Am I correct in thinking that these are external drives?

---

### Post by bthomson100 on 2010-07-23
I think we need to use either LABEL's or UUID's to specify these devices in fstab.

> Am I correct in thinking that these are external drives?

Yes they are. I just noticed via fdisk that the IOMEGA is now sdb1.

What is the syntax for using LABEL or UUED?

Would this apply to USB ports as well? I'm having trouble getting Ubuntu to recognize my Palm device so as to be able to sync it. It worked last week and doesn't now!

bob

---

### Post by bodhi.zazen on 2010-07-23
> **bthomson100 said:**
> I think we need to use either LABEL's or UUID's to specify these devices in fstab.



Yes they are. I just noticed via fdisk that the IOMEGA is now sdb1.

What is the syntax for using LABEL or UUED?

Would this apply to USB ports as well? I'm having trouble getting Ubuntu to recognize my Palm device so as to be able to sync it. It worked last week and doesn't now!

bob

This is why the syntax of fstab has moved away from /dev/sdxy to UUID or lable.

The blkid command shows both the UUID and label

Open fstab and change "/deb/sdb1" to either UUID=xxx or LABEL="DRIVE_LABEL"

See also:

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Morbius1 on 2010-07-23
Let's take this as an example:
```
 /dev/sdb1                     /media/sda1 vfat umask=000  0  0
```[COLOR=Blue]* Am I the only one that thinks that mount point is confusing?*[/COLOR] ;)

To use UUID:
```
 UUID=6BFB-3DFE /media/sda1 vfat umask=000  0  0
```To use LABEL:
```
 LABEL=IOMEGA_HDD /media/sda1 vfat umask=000  0  0
```"FreeAgent Drive" brings up an interesting problem. You can't have spaces like that in the label or the mountpoint in fstab. The way around that is to replace the space with \040 ( That's a zero-4-zero ). So for example if you wanted to create a line in fstab for the free agent drive:

To use UUID:
```
 UUID=D0D03710D036FC72 /media/whatever ntfs defaults,nls=utf8,umask=000 0 0
```To use LABEL:
```
 LABEL=FreeAgent\040Drive /media/whatever ntfs defaults,nls=utf8,umask=000 0 0
```If you have multiple Iomega and Free Agent drives the best approach may be to use UUID's since they are unique.

You do realize I hope that the downside of having these specific fstab entries in fstab for the external drives means that they have to be on and running before you boot. You can add a "user" + "noatuo" option for the vfat entry that will mount it when it's turned on after boot. But that combination doesn't work for the NTFS drive. Unless you have a  reason for having these drives mount to a specific mount point I personally would not have any entry in fstab for the external drives and just let ubuntu mount them when you turn them on.

---

### Post by bthomson100 on 2010-07-24
I've made these changes but now I can't write to disks from Thunderbird, Open Office, GnuCash, etc. This seems to be because I don't have root priviledges but I'm not at all sure since I know so little about Linux. 

All my drives are already/automatically mounted when I restart however. I am able to save files to the Ubuntu directory /home/BobT or any of it's sub-directories so why I can't save to the others is a mystery to me.

[I][B]My stab file now looks like this:
[/B][/I]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc        proc  nodev,noexec,nosuid         0  0  
/host/ubuntu/disks/root.disk  /            ext4  loop,errors=remount-ro      0  1  
/host/ubuntu/disks/swap.disk  none         swap  loop,sw                     0  0  
# /dev/sdb1                     /media/sda1  ntfs  nls=iso8859-1,ro,umask=000  0  0  
# /dev/sdb1                     /media/sda1   vfat  nls=iso8859-1,ro,umask=000  0  0  
LABEL="IOMEGA_HDD"             /media/sdb1 vfat nls=iso8859-1,ro,umask=000  0  0 
# /dev/sdc1                     /media/sdc1    ntfs defaults                    0  0  
LABEL="FreeAgent Drive"       /media/sdc1 ntfs umask=000  0  0
# /dev/sda3                     /media/sda3  ntfs  nls=iso8859-1,ro,umask=000  0  0  
LABEL="DATA"                  /media/sda3  ntfs  nls=iso8859-1,ro,umask=000  0  0 
LABEL="ACER"                  /media/sda2 ntfs nls=iso8859-1,ro,umask=000  0  0


# /dev/sda1                   /media/sda1  
# /dev/sda2                   /media/sda2  FAT16 
# /dev/sda3                   /media/sda3  HPFS/NTFS
# /dev/sdb1                   /media/sdb1  HPFS/NTFS
# /dev/sdc1                   /media/sdc1  W95 FAT32

[B]*fdisk gives me this:*
[/B]
bobt@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41f009f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1147     9213246   27  Unknown
/dev/sda2   *        1148        7889    54155115    6  FAT16
/dev/sda3            7890       14593    53849880    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348278272 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b99a425

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10011    80413326    b  W95 FAT32

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS
bobt@ubuntu:~$ 

***and blkid gives me this:***

bobt@ubuntu:~$ sudo blkid
/dev/loop0: UUID="168c9f8b-21e9-4b86-a9e1-e50e6dfaa0fb" TYPE="ext4" 
/dev/sda1: LABEL="PQSERVICE" UUID="8280B59816D9B5D2" TYPE="ntfs" 
/dev/sda2: LABEL="ACER" UUID="76B81A5DB81A1C65" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="FA7411D27411930D" TYPE="ntfs" 
/dev/sdb1: LABEL="IOMEGA_HDD" UUID="6BFB-3DFE" TYPE="vfat" 
/dev/sdc1: LABEL="FreeAgent Drive" UUID="D0D03710D036FC72" TYPE="ntfs" 
bobt@ubuntu:~$

---

### Post by Morbius1 on 2010-07-24
> LABEL="IOMEGA_HDD"             /media/sdb1 vfat nls=iso8859-1,ro,umask=000  0  0 

LABEL="FreeAgent Drive"       /media/sdc1 ntfs umask=000  0  0

LABEL="DATA"                  /media/sda3  ntfs  nls=iso8859-1,ro,umask=000  0  0 
LABEL="ACER"                  /media/sda2 ntfs nls=iso8859-1,ro,umask=000  0  0(1) remove the ",ro" from each of those
(2) Get rid if the " " around each of the LABEL entries
(3) FreeAgent Drive has to be writen as FreeAgent\040Drive

It should look like this when you're done:
```
LABEL=IOMEGA_HDD /media/sdb1 vfat nls=iso8859-1,umask=000  0  0 
LABEL=FreeAgent\040Drive /media/sdc1 ntfs umask=000  0  0
LABEL=DATA /media/sda3  ntfs  nls=iso8859-1,umask=000  0  0 
LABEL=ACER /media/sda2 ntfs nls=iso8859-1,umask=000  0  0
```

---

### Post by bthomson100 on 2010-07-25
Thanks. I did that and the drives are mounting now. However, the IOMEGA still generates a message when Ubuntu boots sayng I must press S to skip mounting it or M to do it manually. I made sure the IOMEGA was turned on before booting. However, after pressing S to skip, the IOMEGA opened properly when chosen from the Places menu in Ubuntu.

So my problem of writing to Thunderbird etc. is solved which was the most important thing.

---

