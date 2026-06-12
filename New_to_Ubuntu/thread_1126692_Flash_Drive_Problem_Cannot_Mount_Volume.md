---
title: "Flash Drive Problem: Cannot Mount Volume"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by ladybugmandy on 2009-04-15
hello. i am new to linux and have ubuntu 8.04. my USB flash drive will not mount. this is the error i get:

Cannot mount volume
Invalid mount option when attempting to mount the volume.

i have tried going to my main PC (which uses windows) and safely removing the flash drive but it still will not work on my linux PC.

on the advice of someone in another forum, i entered "mount", "df -h", and "dmesg | tail". this is what i got:

sue@sue-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/sue/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sue)
sue@sue-laptop:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 3.3G 2.8G 334M 90% /
varrun 501M 96K 501M 1% /var/run
varlock 501M 0 501M 0% /var/lock
udev 501M 48K 501M 1% /dev
devshm 501M 12K 501M 1% /dev/shm
lrm 501M 39M 463M 8% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon 3.3G 2.8G 334M 90% /home/sue/.gvfs
sue@sue-laptop:~$ dmesg | tail
[ 84.091222] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 84.096041] sd 2:0:0:0: [sdb] 4013713 512-byte hardware sectors (2055 MB)
[ 84.097792] sd 2:0:0:0: [sdb] Write Protect is off
[ 84.097815] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 84.097828] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 84.097848] sdb: sdb1
[ 84.100892] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 84.101079] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 86.724195] UDF-fs: No partition found (1)
[ 86.890825] ISOFS: Unable to identify CD-ROM format


this mini PC does not have a CD-ROM drive.


someone told me to type in "udevinfo -q env -n /dev/sdb1" and this is what i got:

DEVTYPE=partition
ID_VENDOR=SanDisk
ID_MODEL=Cruzer_Slide
ID_REVISION=4.04
ID_SERIAL=SanDisk_Cruzer_Slide_00001675C6754D8D-0:0
ID_SERIAL_SHORT=00001675C6754D8D
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_PATH=pci-0000:00:1d.7-usb-0:1:1.0-scsi-0:0:0:0
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT16
ID_FS_UUID=65DF-0067
ID_FS_UUID_ENC=65DF-0067
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=


any help would be appreciated.

thanks
sue

---

### Post by halitech on 2009-04-15
[color="red"]ID_MODEL=Cruzer_Slide[/color]

Is this a U3 type thumbdrive? If it is, I remember seeing another thread where basically there is a program on the drive that makes it seem like a CDROM and you need to go to the manufactorers website to get the U3 removal tool to run in windows.

---

### Post by taurus on 2009-04-15
What happens when you try to mount it from a terminal with these commands?

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by ladybugmandy on 2009-04-15
i think it was U3 but i have uninstalled the U3 launchpad.

with the command: 

sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h

it get:

mkdir: cannot create directory `/media/sdbl': File exists
sue@sue-laptop:~$ sudo mount -t vfat /dev/sdbl /media/sdbl -o unmask=000 df -h
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

it still won't work.....i get the same error message : cannot mount volume.

---

### Post by halitech on 2009-04-15
try it again but next time, only do 1 comand at a time
```
sudo mount -t vfat /dev/sdbl /media/sdbl -o unmask=000
```
then
```
df -h
```

---

### Post by ladybugmandy on 2009-04-15
this is what happened:

sue@sue-laptop:~$ sudo mount -t vfat /dev/sdbl /media/sdbl -o unmask=000
[sudo] password for sue: 
mount: special device /dev/sdbl does not exist
sue@sue-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.3G  2.9G  331M  90% /
varrun                501M   96K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   48K  501M   1% /dev
devshm                501M   12K  501M   1% /dev/shm
lrm                   501M   39M  463M   8% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      3.3G  2.9G  331M  90% /home/sue/.gvfs




thank you!
sue

---

### Post by halitech on 2009-04-15
I know you say you uninstalled the U3 launchpad but this
```
[ 86.890825] ISOFS: Unable to identify CD-ROM format
```
is leading me to think the drive is still setup with the U3 software

where/how did you uninstall the U3 software?

---

### Post by lamalex on 2009-04-15
> **ladybugmandy said:**
> this is what happened:

sue@sue-laptop:~$ sudo mount -t vfat /dev/sdbl /media/sdbl -o unmask=000
[sudo] password for sue: 
mount: special device /dev/sdbl does not exist

sue

You are typing sdbl as in the letter L, "el". You want to type sdb1 as in the number one (1).

---

### Post by ladybugmandy on 2009-04-15
whoops..sorry!


sue@sue-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o unmask=000
[sudo] password for sue: 
mount: mount point /media/sdb1 does not exist
sue@sue-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.3G  2.9G  331M  90% /
varrun                501M   96K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   48K  501M   1% /dev
devshm                501M   12K  501M   1% /dev/shm
lrm                   501M   39M  463M   8% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      3.3G  2.9G  331M  90% /home/sue/.gvfs


to uninstall U3, i used U3uninstall.exe
thanks!
sue

---

### Post by halitech on 2009-04-15
try this
```
sudo mkdir /media/sdb1
```
you were doing /media/sdbl (lower case L)

---

### Post by ladybugmandy on 2009-04-15
ok so this is what happened. i used the number one and not an L:

sue@sue-laptop:~$ sudo mkdir /media/sdb1
[sudo] password for sue: 
sue@sue-laptop:~$

---

### Post by ladybugmandy on 2009-04-15
i also went to System/Administration/Authorizations and gave myself permission to mount external drives. i don't know if i should have done this but it still doesn't work....

---

### Post by halitech on 2009-04-16
> **ladybugmandy said:**
> ok so this is what happened. i used the number one and not an L:

sue@sue-laptop:~$ sudo mkdir /media/sdb1
[sudo] password for sue: 
sue@sue-laptop:~$

ok, thats good, no errors with making the directory this time. now try to mount it again

```
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o unmask=000
```

---

### Post by ladybugmandy on 2009-04-16
here it is:


sue@sue-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o unmask=000
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


thanks
sue

---

### Post by halitech on 2009-04-16
whats the results of```
sudo fdisk -l
```
thats a lower case L not the number 1

---

### Post by ladybugmandy on 2009-04-16
sue@sue-laptop:~$ sudo fdisk -l
[sudo] password for sue: 

Disk /dev/sda: 3791 MB, 3791241216 bytes
255 heads, 63 sectors/track, 460 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c1a5c1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         433     3478041   83  Linux
/dev/sda2             434         460      216877+   5  Extended
/dev/sda5             434         460      216846   82  Linux swap / Solaris

Disk /dev/sdb: 2055 MB, 2055021056 bytes
16 heads, 63 sectors/track, 3981 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3982     2006825    b  W95 FAT32
sue@sue-laptop:~$

---

### Post by halitech on 2009-04-16
I think I just picked up a spelling mistake

try this

```
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
```

---

### Post by ladybugmandy on 2009-04-16
ok..just to make sure..i used the number ONE here and not an L. also the letter before the word "unmask" is a lower case "o" and not a zero.


sue@sue-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o unmask=000
[sudo] password for sue: 
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


thank you
sue

---

### Post by ladybugmandy on 2009-04-16
hi all. just wanted to let you know that my problem has been solved. someone on another forum told me to use:

sudo mount -t vfat /dev/sdbl /media/sdbl -o unmask=000

then reformat in windows

and it worked!

i hope i won't have this much trouble with linux in the future ...this is very frustrating if you don't know much...

thanks again!
sue

---

### Post by Norcoracer25 on 2009-07-15
Hey ladybug mandy. I have the same problem as you. I have the same problem as you but I cant fix it. I did that command that you said helped you fix it but all the comes up is:

mount: mount point /media/sdbl does not exist

can anyone help. Im on an Asus EEE PC 1000 and Im having major problems with gOS!

---

