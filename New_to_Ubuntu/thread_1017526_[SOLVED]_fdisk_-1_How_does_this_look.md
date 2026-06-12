---
title: "[SOLVED] fdisk -1 How does this look?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-21
How does this look? sdb1 and sdc1 are storage drives. I intended them both to be ext3.

pshootr@LinuxFS:~$ sudo fdisk -l

Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a0469f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2616f054

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1b0b1b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4982    40017883+  83  Linux
pshootr@LinuxFS:~$

---

### Post by ugm6hr on 2008-12-21
sdb appears to have no partitions.

sda is your (small) / directory (4GB) in ext3.

sdc is ext3.

---

### Post by pshootr on 2008-12-21
> **ugm6hr said:**
> sdb appears to have no partitions.

sda is your (small) / directory (4GB) in ext3.

sdc is ext3.

Ok, since then I ran fdisk /dev/sdb and I had a message about a dos partition being made and I used w to write it and now I get this when I do fdisk -1


Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a0469f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2616f054

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1b0b1b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4982    40017883+  83  Linux
pshootr@LinuxFS:~$

It appears I should have done something else as sdb1 has no file system defined. How do I correct this so that it is ext3?

---

### Post by ugm6hr on 2008-12-21
> **pshootr said:**
> It appears I should have done something else as sdb1 has no file system defined. How do I correct this so that it is ext3?

Use cfdisk rather than fdisk.  It is obvious how to do it from there.
```
cfdisk /dev/sdb
```

Or, for GUI, use GParted (System->Admin->Partition Editor.
```
sudo apt-get install gparted
```

---

### Post by pshootr on 2008-12-21
> **ugm6hr said:**
> Use cfdisk rather than fdisk.  It is obvious how to do it from there.
```
cfdisk /dev/sdb
```

Or, for GUI, use GParted (System->Admin->Partition Editor.
```
sudo apt-get install gparted
```

I will have to try cfdisk. As I can not use Gparted, it does not like my riva-TNT2 video card. Thank you.

---

### Post by pshootr on 2008-12-21
Ok, I used cfdisk to re-do sdb and here is what I get from fdisk -1 Does this look correct?


Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a0469f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2616f054

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1b0b1b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4982    40017883+  83  Linux
pshootr@LinuxFS:~$

---

### Post by pshootr on 2008-12-21
Now when I try and download a 4.3 gig torrent to sdb1 (40 gig drive) Utorrent tells me there is not enough space on the drive, and would I like to continue anyway. Why am I getting this message?

---

### Post by pshootr on 2008-12-21
:-\"

---

### Post by pshootr on 2008-12-21
anybody?

---

### Post by bumanie on 2008-12-21
Post the output of > df -h 

---

### Post by pshootr on 2008-12-21
> **bumanie said:**
> Post the output of

pshootr@LinuxFS:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.8G  777M  2.8G  22% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  324K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.7M  249M   2% /dev
tmpfs                 252M     0  252M   0% /dev/shm

Does not give info on storage drives.

---

### Post by pshootr on 2008-12-21
may be because it only looks at /media? My storage drives are mounted to /mnt. Does this mean I should use another command to view free space on the storage drives?

---

### Post by bumanie on 2008-12-21
Post the output of > mounti suspect that the download can only see that there are 2.8gb left on sda and has no idea that there is sdb and sdc - you need to ensure that they can be mounted and then you will have to direct the torrent output to go a file you have prepared there ie make a file named Download (or something similar). You can either mount the drives manually via terminal or via GUI through Places or have them auto mount if they are added to /etc/fstab.

PS: You beat me to getting an answer out. Anyway still post the output of mount command, please.

---

### Post by pshootr on 2008-12-21
> **bumanie said:**
> Post the output of i suspect that the download can only see that there are 2.8gb left on sda and has no idea that there is sdb and sdc - you need to ensure that they can be mounted and then you will have to direct the torrent output to go a file you have prepared there ie make a file named Download (or something similar). You can either mount the drives manually via terminal or via GUI through Places or have them auto mount if they are added to /etc/fstab.

PS: You beat me to getting an answer out. Anyway still post the output of mount command, please.

here is my fstab


pshootr@LinuxFS:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=77f2e095-20b5-44a1-9bdd-a6830cb8c3f0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ba12429d-218c-4f45-bb80-90594c29f597 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
pshootr@LinuxFS:~$


Funny thing is, storage drives appear to be mounted as I can access them from my windows machine via samba. I am using uTorrent on my windows machine, and saving files to the mounted storage drives on the linux server box. Which has my storage drives in it. So here is my download path
\\Linuxfs\sdb1 on linuxfs\torrent_imports

---

### Post by pshootr on 2008-12-21
Ok here is what I get after mount command

pshootr@LinuxFS:~$ mount
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
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by pshootr on 2008-12-21
sorry for the delay. My mount command ouput is one post up.

---

### Post by bumanie on 2008-12-21
Well, from what I can tell from the output of mount and your /etc/fstab, neither sdb nor sdc are mounted - sorry I know nothing about samba and how to route things through to linux from windows, so I can't comment there. fstab basically lists all available partitions and storage devices - the only ones you have mentioned are sda1 (main ubuntu filesystem), sda5 (swap) and your cdrom/dvd drive. This is starting to get a little outside my area of knowledge, but if I were you, I would try and move /home to one of the data drives, rather than have /home reisde on the same partition as /. But that is up to you - it would save some difficulties to have /home on its own hard drive.

---

### Post by pshootr on 2008-12-21
I don't know why the mount command only shows my boot drive. But I do know that I would not be able to write to the storage drives if they were not mounted... And I can write to them.

---

### Post by pshootr on 2008-12-21
All samba does is allow me to share these storage drives with windows users. It does not change the way they are mounted.

---

### Post by pshootr on 2008-12-21
Just to be clear, samba is working fine. And I am able to read/write to the storage drives from my widows machine. Which indicates that the storage drives ARE mounted. Now this makes me wonder why storage drives do not show up when I do the 'mount' command. After I recieved the message from uTorrent about there not being enough space on sdb1, I chose to continue anyway and the download is working. I just don't understand 1. how come I get that message in the first place. and 2. Why 'mount' command only shows my boot drive 'sda'

---

### Post by carml on 2008-12-21
If you want to edit your partitions,I think you can use also the Live version of Gparted,which allows you to manipulate all the existing partitions.All you need to do is to download it,burn to a disk(it's quite 50 MB),reboot with the disk inserted on the CD/DVD reader. :P

---

### Post by pshootr on 2008-12-21
> **carml said:**
> If you want to edit your partitions,I think you can use also the Live version of Gparted,which allows you to manipulate all the existing partitions.All you need to do is to download it,burn to a disk(it's quite 50 MB),reboot with the disk inserted on the CD/DVD reader. :P

I can not use gparted. It does not like my video card. Or maybe it is just because I am using 8.10 server not desktop, CLI only.
Now I did boot from a live cd and reformat my storage drives from partition manager.

---

### Post by ugm6hr on 2008-12-21
> **pshootr said:**
> I don't know why the mount command only shows my boot drive. But I do know that I would not be able to write to the storage drives if they were not mounted... And I can write to them.

That does not make sense.  It certainly appears like they are not mounted.  Are you certain you are actually writing to sdb1 and not in sda1?

Try unmounting:
```
sudo umount /dev/sdb1
```

If it is not currently mounted, it will tell you so.

And mount manually:
```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
```

PS: GParted will not work without an x session (i.e. no GUI will work with Ubuntu Server).

---

### Post by pshootr on 2008-12-21
> **ugm6hr said:**
> That does not make sense.  It certainly appears like they are not mounted.  Are you certain you are actually writing to sdb1 and not in sda1?

Try unmounting:
```
sudo umount /dev/sdb1
```

If it is not currently mounted, it will tell you so.

And mount manually:
```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
```

PS: GParted will not work with an x session (i.e. no GUI will work with Ubuntu Server).

Ok, let me put it to you this way. I am currently on my windows machine. And I am looking at \\Linuxfs\sdb1 on linuxfs\torrent_imports 'via samba'

And uTorrent is currently writeing data to that path.

---

### Post by carml on 2008-12-21
@ all
Sorry,I thought it would run anyway,I'm used with the Desktop version. 
#-o

---

### Post by ugm6hr on 2008-12-21
> **pshootr said:**
> Ok, let me put it to you this way. I am currently on my windows machine. And I am looking at \\Linuxfs\sdb1 on linuxfs\torrent_imports 'via samba'

And uTorrent is currently writeing data to that path.

Unfortunately, I have little (i.e. no) Samba experience.  But I suspect \\Linuxfs\sdb1 is a shortcut to somewhere; it is possible that it is a shortcut to somewhere other than /dev/sdb1.

Try writing to sdb1 from Linux.

The following will check HD space definitively:

```
df /dev/sdb1 -h
df /mnt/sdb1 -h
```

If not mounted, it will report back on /dev (udev)

---

### Post by pshootr on 2008-12-21
> **ugm6hr said:**
> Unfortunately, I have little (i.e. no) Samba experience.  But I suspect \\Linuxfs\sdb1 is a shortcut to somewhere; it is possible that it is a shortcut to somewhere other than /dev/sdb1.

Try writing to sdb1 from Linux.

The following will check HD space definitively:

```
df /dev/sdb1 -h
df /mnt/sdb1 -h
```

If not mounted, it will report back on /dev (udev)

pshootr@LinuxFS:~$ df /dev/sdb1 -h
Filesystem            Size  Used Avail Use% Mounted on
udev                  252M  2.7M  249M   2% /dev
pshootr@LinuxFS:~$ df /mnt/sdb1 -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.8G  884M  2.7G  25% /
pshootr@LinuxFS:~$

---

### Post by pshootr on 2008-12-21
pshootr@LinuxFS:~$ nano /mnt/sdb1/testfile
pshootr@LinuxFS:~$ cat /mnt/sdb1/testfile
test

Yes I can write to sdb1 from linux

ie: using ssh from my windows machine.

---

### Post by ugm6hr on 2008-12-21
> **pshootr said:**
> pshootr@LinuxFS:~$ df /dev/sdb1 -h
Filesystem            Size  Used Avail Use% Mounted on
udev                  252M  2.7M  249M   2% /dev
pshootr@LinuxFS:~$ df /mnt/sdb1 -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.8G  884M  2.7G  25% /
pshootr@LinuxFS:~$

This appears to suggest that:
1. sdb1 is NOT mounted (see first command - /dev details rather than /dev/sdb1.
2. /mnt/sdb1 is part of / (i.e. /dev/sda1) rather than a separate partition.

Hence, you have a directory called /mnt/sdb1 but it is exactly that - a directory within / (sda1), not sdb1.

This should mount it to there for you:
```
sudo mount /dev/sdb1 /mnt/sdb1
```

---

### Post by pshootr on 2008-12-21
> **ugm6hr said:**
> This appears to suggest that:
1. sdb1 is NOT mounted (see first command - /dev details rather than /dev/sdb1.
2. /mnt/sdb1 is part of / (i.e. /dev/sda1) rather than a separate partition.

Hence, you have a directory called /mnt/sdb1 but it is exactly that - a directory within / (sda1), not sdb1.

This should mount it to there for you:
```
sudo mount /dev/sdb1 /mnt/sdb1
```


pshootr@LinuxFS:~$ sudo mount /dev/sdb1 /mnt/sdb1
[sudo] password for pshootr:
mount: you must specify the filesystem type
pshootr@LinuxFS:~$
 
whats missing here?

---

### Post by pshootr on 2008-12-21
Well I tried  pshootr@LinuxFS:~$ sudo mount /dev/sdb1 /mnt/sdb1 ext3  

And I got this below.

pshootr@LinuxFS:~$ sudo mount /dev/sdb1 /mnt/sdb1 ext3
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
pshootr@LinuxFS:~$ df /mnt/sdb1 -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.8G  905M  2.7G  25% /
pshootr@LinuxFS:~$

---

### Post by pshootr on 2008-12-21
:-\"

---

### Post by pshootr on 2008-12-21
> **ugm6hr said:**
> This appears to suggest that:
1. sdb1 is NOT mounted (see first command - /dev details rather than /dev/sdb1.
2. /mnt/sdb1 is part of / (i.e. /dev/sda1) rather than a separate partition.

Hence, you have a directory called /mnt/sdb1 but it is exactly that - a directory within / (sda1), not sdb1.

This should mount it to there for you:
```
sudo mount /dev/sdb1 /mnt/sdb1
```

Here is what I get when I do 'sudo mount /dev/sdb1 /mnt/sdb1'


pshootr@LinuxFS:~$ sudo mount /dev/sdb1 /mnt/sdb1
mount: you must specify the filesystem type
pshootr@LinuxFS:~$

How should I specify the filesystem?

---

### Post by unutbu on 2008-12-21
Hi pshootr. :) 
First, perhaps you should move what data you have in /mnt/sdb1 to a different temporary directory. When we get the sdb1 partition to mount at /mnt/sdb1, its contents are going to "cover up" sda's version of /mnt/sdb1 and then sda is going to have space missing for no good reason.

Next, I believe the problem is that fdisk (or cfdisk) edits the partition table, but does not create a filesystem within the partition. So to create a ext3 filesystem, type this:
```

sudo mkfs.ext3 -m0 /dev/sdb1
```
Note this will erase anything that might be on /dev/sdb1. If I understand your situation correctly, it is currently empty.

Now try to mount the drive with the command
```

sudo mount /dev/sdb1 /mnt/sdb1
```

---

### Post by pshootr on 2008-12-21
> **unutbu said:**
> Hi pshootr. :) 
First, perhaps you should move what data you have in /mnt/sdb1 to a different temporary directory. When we get the sdb1 partition to mount at /mnt/sdb1, its contents are going to "cover up" sda's version of /mnt/sdb1 and then sda is going to have space missing for no good reason.

Next, I believe the problem is that fdisk (or cfdisk) edits the partition table, but does not create a filesystem within the partition. So to create a ext3 filesystem, type this:
```

sudo mkfs.ext3 -m0 /dev/sdb1
```
Note this will erase anything that might be on /dev/sdb1. If I understand your situation correctly, it is currently empty.

Now try to mount the drive with the command
```

sudo mount /dev/sdb1 /mnt/sdb1
```

I skipped the file moving part, and just deleted the data, as it was not important. Then I did as you asked for both storage drives.. And sdb1 as well as  sdc1 seem to be mounted properly now.
  Thank you very much. Now how can I be sure that both these storage drives will be mounted at every reboot?

---

### Post by unutbu on 2008-12-21
Ah. Good question. Please post
```

blkid
```

---

### Post by pshootr on 2008-12-21
> **unutbu said:**
> Ah. Good question. Please post
```

blkid
```


pshootr@LinuxFS:~$ blkid
/dev/sda1: UUID="77f2e095-20b5-44a1-9bdd-a6830cb8c3f0" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="ba12429d-218c-4f45-bb80-90594c29f597"
/dev/sdb1: UUID="ea659ec9-5ee6-4c46-9e02-4eaeb0a76d7c" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdc1: UUID="1bd5aea3-731d-4c4b-95ed-ca7bbcfe3c9a" SEC_TYPE="ext2" TYPE="ext3"
pshootr@LinuxFS:~$

---

### Post by pshootr on 2008-12-21
bump

---

### Post by unutbu on 2008-12-21
```
gksu gedit /etc/fstab
```

Edit your /etc/fstab file to look like this. (The 4 lines at the bottom are new).

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=77f2e095-20b5-44a1-9bdd-a6830cb8c3f0 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=ba12429d-218c-4f45-bb80-90594c29f597 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sdb1
UUID=ea659ec9-5ee6-4c46-9e02-4eaeb0a76d7c /mnt/sdb1 ext3 relatime,errors=remount-ro 0 2
# /dev/sdc1
UUID=1bd5aea3-731d-4c4b-95ed-ca7bbcfe3c9a /mnt/sdc1 ext3 relatime,errors=remount-ro 0 2
```

To test it out, reboot the machine. /dev/sdb1 will be mounted at
/mnt/sdb1 and /dev/sdc1 will be mounted at /mnt/sdc1.

---

### Post by pshootr on 2008-12-21
> **unutbu said:**
> ```
gksu gedit /etc/fstab
```

Edit your /etc/fstab file to look like this. (The 4 lines at the bottom are new).

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=77f2e095-20b5-44a1-9bdd-a6830cb8c3f0 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=ba12429d-218c-4f45-bb80-90594c29f597 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sdb1
UUID=ea659ec9-5ee6-4c46-9e02-4eaeb0a76d7c /mnt/sdb1 ext3 relatime,errors=remount-ro 0 2
# /dev/sdc1
UUID=1bd5aea3-731d-4c4b-95ed-ca7bbcfe3c9a /mnt/sdc1 ext3 relatime,errors=remount-ro 0 2
```

To test it out, reboot the machine. /dev/sdb1 will be mounted at
/mnt/sdb1 and /dev/sdc1 will be mounted at /mnt/sdc1.

Ok, I used nano to edit the fstab file like you suggested. And upon reboot I get errors about some 'chk' failing. I have to press ctrl-d to continue booting. After doing that and booting, the mount command does not show sdb1 or sdb2. sigh

---

### Post by pshootr on 2008-12-21
I just removed the added lines from fstab to see if I get the error upon booing. Should know in a minute.

---

### Post by unutbu on 2008-12-21
How about post```

sudo tune2fs -l /dev/sdb1
sudo tune2fs -l /dev/sdc1
```
This will give us some information about the current state of the filesystem (if it is clean or corrupt) and should confirm the UUIDs.

---

### Post by pshootr on 2008-12-21
> **unutbu said:**
> How about post```

sudo tune2fs -l /dev/sdb1
sudo tune2fs -l /dev/sdc1
```
This will give us some information about the current state of the filesystem (if it is clean or corrupt) and should confirm the UUIDs.

Ok, removing the added lines to fstab has solved the boot error.

And now here is the output you last asked for.


pshootr@LinuxFS:~$ sudo tune2fs -l /dev/sdb1
tune2fs 1.41.3 (12-Oct-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          7e382039-d9b9-4886-8638-ef8726df4f3c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              2444624
Block count:              9769520
Reserved block count:     0
Free blocks:              9571026
Free inodes:              2444613
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1021
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8176
Inode blocks per group:   511
Filesystem created:       Sun Dec 21 11:31:10 2008
Last mount time:          Sun Dec 21 11:33:29 2008
Last write time:          Sun Dec 21 12:18:48 2008
Mount count:              1
Maximum mount count:      23
Last checked:             Sun Dec 21 11:31:10 2008
Check interval:           15552000 (6 months)
Next check after:         Fri Jun 19 12:31:10 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      b8bb4cb3-b75f-450a-a2d9-e690a1b1cde9
Journal backup:           inode blocks
pshootr@LinuxFS:~$


 
pshootr@LinuxFS:~$ sudo tune2fs -l /dev/sdc1
tune2fs 1.41.3 (12-Oct-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          e3ebba7c-443b-4c11-baf0-2944372c420e
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              2501856
Block count:              10004470
Reserved block count:     0
Free blocks:              9802385
Free inodes:              2501845
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1021
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8176
Inode blocks per group:   511
Filesystem created:       Sun Dec 21 11:32:13 2008
Last mount time:          Sun Dec 21 11:33:52 2008
Last write time:          Sun Dec 21 12:18:48 2008
Mount count:              1
Maximum mount count:      26
Last checked:             Sun Dec 21 11:32:13 2008
Check interval:           15552000 (6 months)
Next check after:         Fri Jun 19 12:32:13 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      0b3b506f-8332-458d-9df0-fb658b78a070
Journal backup:           inode blocks
pshootr@LinuxFS:~$

---

### Post by pshootr on 2008-12-21
bump

---

### Post by unutbu on 2008-12-21
Okay, I think I know what went wrong. I believe that when you make a new filesystem blkid does not update to reflect that change. So when I asked you for the output of blkid, we were getting old information. The tune2fs commands I think are giving the correct UUIDs. (By the way, tune2fs is reporting that your filesystems are clean, which is good too).

So please edit /etc/fstab again:
```

gksu gedit /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=77f2e095-20b5-44a1-9bdd-a6830cb8c3f0 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=ba12429d-218c-4f45-bb80-90594c29f597 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sdb1
UUID=**7e382039-d9b9-4886-8638-ef8726df4f3c** /mnt/sdb1 ext3 relatime,errors=remount-ro 0 2
# /dev/sdc1
UUID=**e3ebba7c-443b-4c11-baf0-2944372c420e** /mnt/sdc1 ext3 relatime,errors=remount-ro 0 2
```
The only thing I changed was the UUIDs.
Let us know how it goes.

---

### Post by pshootr on 2008-12-21
> **unutbu said:**
> Okay, I think I know what went wrong. I believe that when you make a new filesystem blkid does not update to reflect that change. So when I asked you for the output of blkid, we were getting old information. The tune2fs commands I think are giving the correct UUIDs. (By the way, tune2fs is reporting that your filesystems are clean, which is good too).

So please edit /etc/fstab again:
```

gksu gedit /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=77f2e095-20b5-44a1-9bdd-a6830cb8c3f0 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=ba12429d-218c-4f45-bb80-90594c29f597 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sdb1
UUID=**7e382039-d9b9-4886-8638-ef8726df4f3c** /mnt/sdb1 ext3 relatime,errors=remount-ro 0 2
# /dev/sdc1
UUID=**e3ebba7c-443b-4c11-baf0-2944372c420e** /mnt/sdc1 ext3 relatime,errors=remount-ro 0 2
```
The only thing I changed was the UUIDs.
Let us know how it goes.

Well after editing stab again, I am no longer able to boot at all. No error nothing. Just a blinking cursor. I will try a couple more times to reboot.

---

### Post by unutbu on 2008-12-21
Go to the BIOS menu and make sure the boot order is such that the sda drive is set to boot first. This is the only thing that I can think of which would cause you to get a black screen with a blinking cursor.

---

### Post by pshootr on 2008-12-21
Ok, took a couple of tries but she is fired up again. Hope I didn't scare you too bad :lolflag:

Now 'mount command gives me this. Looks good eh..


pshootr@LinuxFS:~$ mount
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
/dev/sdb1 on /mnt/sdb1 type ext3 (rw,relatime,errors=remount-ro)
/dev/sdc1 on /mnt/sdc1 type ext3 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw)
pshootr@LinuxFS:~$

---

### Post by pshootr on 2008-12-21
First off, thank you very much for all your time/patiance/and effort. Now I have one more issue. I need to know how I can make both of these storage drives writable from my windows machine after every reboot.

---

### Post by pshootr on 2008-12-21
> **pshootr said:**
> First off, thank you very much for all your time/patiance/and effort. Now I have one more issue. I need to know how I can make both of these storage drives writable from my windows machine after every reboot.

will this do it?

chmod 777 /mnt/sdb1

---

### Post by unutbu on 2008-12-21
Okay, I can answer half of this question with confidence, the other half is a guess.

To make the partitions writable for you as a normal user:
```

sudo chown -R $USER:$USER /mnt/sdb1
sudo chown -R $USER:$USER /mnt/sdc1
sudo chmod u=rwx /mnt/sdb1
sudo chmod u=rwx /mnt/sdc1

```

The first two commands make you the owner of the /mnt/sdb1, /mnt/sdc1 directories.

The last two commands give you permissions to read,write and execute the same directories.

The other half of the problem concerns setting up Samba. 
I have no experience with this. The instructions on this page seem pretty clear however: [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide). Note in particular the section entitled "Registering Our Shares":

```
//DEVMACHINE/shares     /media/winshares        cifs   auto,credentials=/etc/smbcredentials,workgroup=MSHOME,gid=smb,uid=1000,file_mode=770,dir_mode=770,rw       0       0
```

I'd suggest going through all the instructions from the top so you get Samba configured properly. Best of luck!

---

### Post by pshootr on 2008-12-21
> **unutbu said:**
> Okay, I can answer half of this question with confidence, the other half is a guess.

To make the partitions writable for you as a normal user:
```

sudo chown -R $USER:$USER /mnt/sdb1
sudo chown -R $USER:$USER /mnt/sdc1
sudo chmdo u=rwx /mnt/sdb1
sudo chmdo u=rwx /mnt/sdc1

```

The first two commands make you the owner of the /mnt/sdb1, /mnt/sdc1 directories.

The last two commands give you permissions to read,write and execute the same directories.

The other half of the problem concerns setting up Samba. 
I have no experience with this. The instructions on this page seem pretty clear however: [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide). Note in particular the section entitled "Registering Our Shares":

```
//DEVMACHINE/shares     /media/winshares        cifs   auto,credentials=/etc/smbcredentials,workgroup=MSHOME,gid=smb,uid=1000,file_mode=770,dir_mode=770,rw       0       0
```

I'd suggest going through all the instructions from the top so you get Samba configured properly. Best of luck!

I used to first two commands 'sudo chown -R $USER:$USER /mnt/sdb1
sudo chown -R $USER:$USER /mnt/sdc1' and it did change the owner to my user name. And rite away I was able to create a new directory inside sdb1. This is good. Now I am testing to see see if uTorrent is able to write to that new folder.

EDIT: uTorrent has failed to write to the newly made dir.

---

### Post by pshootr on 2008-12-21
first time i tried sudo chmdo* u=rwx /mnt/sdb1
sudo chmdo* u=rwx /mnt/sdc1

I got no such command. Then realized there was a typo. So I corrected the typo and am now testing my write permissions again.

---

### Post by pshootr on 2008-12-21
Yes, it appears that have to reconfigure samba. Thank you so much for your help. And also for the link on setting samba up. You :guitar:

---

### Post by pshootr on 2008-12-21
Update: I did 'sudo chmod 777 /mnt/sdb1/uTorrent_exports'

This seems to have worked. It does not appear that I have to do anything to samba. I just wonder if these permissions will change after I reboot the server?

---

### Post by unutbu on 2008-12-21
No change necessary. The chmod command alters the ext3 filesystem, and the filesystem remembers its state.

Congratulations!

---

### Post by pshootr on 2008-12-21
> **unutbu said:**
> No change necessary. The chmod command alters the ext3 filesystem, and the filesystem remembers its state.

Congratulations!

Dude, thank you soooooo much. Like I said you :guitar: man

---

