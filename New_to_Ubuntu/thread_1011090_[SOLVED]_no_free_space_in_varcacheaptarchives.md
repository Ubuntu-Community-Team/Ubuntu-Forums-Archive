---
title: "[SOLVED] no free space in /var/cache/apt/archives/?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Papa-san on 2008-12-14
I'm trying to install java 6, and get this message:
```
john@john-desktop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  java-common odbcinst1debian1 unixodbc
Suggested packages:
  equivs binfmt-support sun-java6-fonts libct1 libmyodbc odbc-postgresql
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  java-common odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin
  unixodbc
0 upgraded, 6 newly installed, 0 to remove and 4 not upgraded.
Need to get 34.0MB/34.1MB of archives.
After this operation, 98.0MB of additional disk space will be used.
E: You don't have enough free space in /var/cache/apt/archives/.
john@john-desktop:~$ 
```I have opened that folder, and there are many un-necessary  .deb files, but I cannot get rid of them.
Is there a proper way to remove them?

---

### Post by logos34 on 2008-12-14
sudo apt-get autoclean

if that doesn't free up enough space, then

sudo apt-get clean

(clears out ALL .debs downloaded and/or installed)

---

### Post by bluefrog on 2008-12-14
sudo apt-get autoclean or clean to get rid of everything

can use synaptic/pref -files "delete package..."

---

### Post by taurus on 2008-12-14
How large is your / partition anyway?  Make sure you don't have some backup files in /var/backups taking up valuable space.

```
df -h
sudo du -h /var/backups
```

---

### Post by Papa-san on 2008-12-14
Thanks!
The autoclean wasn't enough, so I used the ```
sudo apt get clean
``` and it worked like a charm!

Hi Taurus...
```
john@john-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             2.9G  2.6G  192M  94% /
varrun                474M  100K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   76K  474M   1% /dev
devshm                474M   52K  474M   1% /dev/shm
lrm                   474M   39M  435M   9% /lib/modules/2.6.24-22-generic/volatile
/dev/sda4              12G  252M   12G   3% /home
overflow              1.0M   64K  960K   7% /tmp
gvfs-fuse-daemon      2.9G  2.6G  192M  94% /home/john/.gvfs
/dev/sdb1             2.0G  1.1G  915M  54% /media/disk-1
john@john-desktop:~$ 

```var/backups is 4.2M

---

### Post by rakris on 2008-12-14
And if you have not installed way too many packages, you could be running out of root space soon. 

I suggest you check it.

---

### Post by Papa-san on 2008-12-14
Does that mean that my root partition is only 2.6G ?
When I partitioned my drive, I selected 19G for Ubuntu, and 12G for win XP.

And if so, how do I clean it up?

---

### Post by taurus on 2008-12-14
> 
john@john-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda2             2.9G  2.6G  192M  94% /[/COLOR]**
varrun                474M  100K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   76K  474M   1% /dev
devshm                474M   52K  474M   1% /dev/shm
lrm                   474M   39M  435M   9% /lib/modules/2.6.24-22-generic/volatile
/dev/sda4              12G  252M   12G   3% /home
overflow              1.0M   64K  960K   7% /tmp
gvfs-fuse-daemon      2.9G  2.6G  192M  94% /home/john/.gvfs
/dev/sdb1             2.0G  1.1G  915M  54% /media/disk-1
john@john-desktop:~$

Looks like you don't give yourself, /, a whole lot of space.  Therefore, you need to constantly clean out your cache or you will be getting a message about running out of space on /.

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Papa-san on 2008-12-14
```
john@john-desktop:~$ sudo fdisk -l
[sudo] password for john: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13721371

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21500608+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2678        3053     3020220   83  Linux
/dev/sda3            3054        3296     1951897+  82  Linux swap / Solaris
/dev/sda4            3297        4865    12602992+  83  Linux

Disk /dev/sdb: 2047 MB, 2047678976 bytes
64 heads, 63 sectors/track, 991 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         991     1997733+   b  W95 FAT32
john@john-desktop:~$ 

```

---

### Post by taurus on 2008-12-14
I guess you can use gparted from the LiveCD (System -> Administration) to shrink the ntfs partition, /dev/sda1, and give that space to Ubuntu, /dev/sda2.  Of course, you _should_ backup your important files first before you resize anything.  Also, may want to boot into windows and defrag the windows partition a couple of times before shrinking it with gparted.

---

### Post by Papa-san on 2008-12-14
OK,

Thank you very much!

I'll do that, and hopefully it will work out alright. 
(I typically find your advice to be reliable!)

---

