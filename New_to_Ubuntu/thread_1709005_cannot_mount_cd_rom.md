---
title: "cannot mount cd rom"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by rocketmitra on 2011-03-17
I've installed ubuntu 10.10  by a live CD with the help of my dvd writer alongside windows xp,but after installation when i put cd/dvd in my dvd writer it says cannot mount cd rom and gives error...pl help as i cannot run any cd/dvd...#-o

---

### Post by TeoBigusGeekus on 2011-03-17
Could you please post us the exact error it gives you?

---

### Post by rocketmitra on 2011-03-17
Error scanning the CD
E:Failed to mount the cdrom

---

### Post by TeoBigusGeekus on 2011-03-17
Have you tried with different cds/dvds?

---

### Post by rocketmitra on 2011-03-17
how can i make work autocad civil 3d and Archicad ...i've located them but there are nothing to load

---

### Post by TeoBigusGeekus on 2011-03-17
> **rocketmitra said:**
> how can i make work autocad civil 3d and Archicad 
That's my signature; ignore it.
Have you tried with different cds/dvds?

---

### Post by rocketmitra on 2011-03-17
yes i've tried different cd /dvd rom....the computer option shows 4 drives with files which is like i see on windows xp  but not the dvd drive as in windows xp

---

### Post by TeoBigusGeekus on 2011-03-17
Ok, put a cd/dvd in and post us the output of the following commands
```
sudo fdisk -l
```
```
mount
```
and
```
ls /media/
```

---

### Post by rocketmitra on 2011-03-17
udayan@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9a8e9a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11621    93345651    7  HPFS/NTFS
/dev/sda2           11622       38912   219214957+   f  W95 Ext'd (LBA)
/dev/sda5           11622       19448    62870346    7  HPFS/NTFS
/dev/sda6           19449       29647    81923436    7  HPFS/NTFS
/dev/sda7           29648       36404    54275571    7  HPFS/NTFS
/dev/sda8           36405       38912    20145478+   7  HPFS/NTFS
udayan@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/udayan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=udayan)
/dev/sda6 on /media/CE90FDEE90FDDD41 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5 on /media/2E54F74F54F717F3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7 on /media/147004D97004C408 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8 on /media/606823756823495C type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
udayan@ubuntu:~$ ls /media/
147004D97004C408  2E54F74F54F717F3  606823756823495C  apt  CE90FDEE90FDDD41
udayan@ubuntu:~$

---

### Post by TeoBigusGeekus on 2011-03-17
Hmmm....
Have you let the disk to be recognized by the system?
Cause nothing appears in there.
Give us the output of the commands again after you've waited for some seconds for the disk to be recognized.

---

### Post by rocketmitra on 2011-03-17
[COLOR=#ff0000][COLOR=Black]This is the message i received when i tried to play dvd by VLC player[/COLOR][/COLOR]
[COLOR=#ff0000][COLOR=Black]************************************************************************************[/COLOR]
[/COLOR]
[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/dvd".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.[/COLOR]


[COLOR=#000000]These are the findings of the codes[/COLOR]
[COLOR=#000000]*****************************************************
[/COLOR]
udayan@ubuntu:~$ sudo fdisk -l
[sudo] password for udayan: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9a8e9a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11621    93345651    7  HPFS/NTFS
/dev/sda2           11622       38912   219214957+   f  W95 Ext'd (LBA)
/dev/sda5           11622       19448    62870346    7  HPFS/NTFS
/dev/sda6           19449       29647    81923436    7  HPFS/NTFS
/dev/sda7           29648       36404    54275571    7  HPFS/NTFS
/dev/sda8           36405       38912    20145478+   7  HPFS/NTFS
udayan@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/udayan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=udayan)
/dev/sda6 on /media/CE90FDEE90FDDD41 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5 on /media/2E54F74F54F717F3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7 on /media/147004D97004C408 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8 on /media/606823756823495C type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
udayan@ubuntu:~$ ls /media/
147004D97004C408  2E54F74F54F717F3  606823756823495C  apt  CE90FDEE90FDDD41
udayan@ubuntu:~$

---

### Post by TeoBigusGeekus on 2011-03-17
Let's try this then:
```
sudo mkdir /media/dvd
```
to create a folder to mount the disk. Then
```
sudo mount /dev/dvd /media/dvd
```
to attempt to mount it.
If that fails, replace /dev/dvd with /dev/sr0.

---

### Post by rocketmitra on 2011-03-17
These are the findings
*******************************
udayan@ubuntu:~$ sudo mkdir  /media/dvd
[sudo] password for udayan: 
mkdir: cannot create directory `/media/dvd': File exists
udayan@ubuntu:~$ sudo mount  /dev/dvd  /media/dvd
mount: special device /dev/dvd does not exist
udayan@ubuntu:~$ sudo mount  /dev/sr0  /media/dvd
mount: special device /dev/sr0 does not exist
udayan@ubuntu:~$

---

### Post by TeoBigusGeekus on 2011-03-17
What about
```
sudo mount /dev/cd /media/dvd
```
?

---

### Post by rocketmitra on 2011-03-17
udayan@ubuntu:~$ sudo mount /dev/cd /media/dvd
mount: special device /dev/cd does not exist

---

### Post by TeoBigusGeekus on 2011-03-17
I give up. Sorry mate...
Anyone else?

---

### Post by rocketmitra on 2011-03-17
Thnx for atleast tring...will search around but if u come accross solution pl post it

---

