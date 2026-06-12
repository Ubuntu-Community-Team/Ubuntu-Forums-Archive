---
title: "Mounting hard drives Natty Narwhal 11.04"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by marcoftheknight on 2011-06-01
I recently tried mounting my hard drives using some code and different reasources. I think I did it incorrectly :) no clue what i did (mkdir media ect..). 

Later I went to -->systems--> Hard drive management and found that you could mount hard drives easily with that utility. I went to find the files on the hard drive but they did not appear. The 4 other extra hardrive are windows formated NTFS (2 Dynamic 1 normal ) why cant I see all my windows files? Even though in the Hard drive management area it shows that they mounted and have the correct sizing.

Thanks

---

### Post by seawolf167 on 2011-06-01
Please post the output of 

```
mount
sudo fdisk -l
sudo blkid
```so we can see what you have mounted (and give you an /etc/fstab entry). you may have to remove some mount points if the device exists elsewhere

as an FYI, the command line way to mount a device is to first create a directory to mount the device in

```
sudo mkdir /media/mymountpoint
```then actually mount the device

```
sudo mount /dev/sda1 /media/mymountpoint
```where /dev/sda1 is the partition you want to mount, which you can find out from 

```
sudo fdisk -l
```

---

### Post by marcoftheknight on 2011-06-05
I apologize for not posting this immediately but Been on my windows machine and still haven't figured out how to allow for selection of which OS to boot. I have to press F12 still and select which hard drive to boot from. Secondly I got starcrat 2 working but it crash with SOIS. ( storm of the imperial sanctum which is one of my favorite custom and there's no solution posted yet on there forums.) 
I will leave the site open on my other monitor and will be waiting for a reply going to try to get this figured out today hopefully.

Thanks great linux people

-GA-890GPA-UD3H:~$ mount
/dev/sde1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdc2 on /media/sdc2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/sdd1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /media/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marc)
/dev/sr0 on /media/SC2-L100-D1 type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)

-GA-890GPA-UD3H:~$ sudo fdisk -l


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c58e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77826   625130808+  42  SFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008cce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121602   976761528+  42  SFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009fc5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         399     3196928    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2             399       77826   621932544    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000904a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       64602   488383488    7  HPFS/NTFS

Disk /dev/sde: 55.0 GB, 55021510656 bytes
255 heads, 63 sectors/track, 6689 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000205ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        5124    41150464   83  Linux
/dev/sde2            5124        6690    12578817    5  Extended
/dev/sde5            5124        6690    12578816   82  Linux swap / Solaris
:~$ sudo blkid
/dev/sda2: UUID="6620178343C8AB1F" TYPE="ntfs" 
/dev/sdc2: LABEL="New Volume" UUID="E2A6931FA692F2F1" TYPE="ntfs" 
/dev/sdb1: LABEL="Disk 0 640GB" UUID="FE1647DD16479615" TYPE="ntfs" 
/dev/sdb2: UUID="E4D4D6A2D4D675F0" TYPE="ntfs" 
/dev/sdd1: LABEL="fdrive" UUID="A88E81698E81313C" TYPE="ntfs" 
/dev/sde1: UUID="e9d5d19e-8606-4bce-966b-3660f3a2df20" TYPE="ext4" 
/dev/sde5: UUID="3155e941-f6d7-419c-914e-4c4ef55f46f8" TYPE="swap"

---

### Post by marcoftheknight on 2011-06-05
Unmounted the sdc1 in the drivemanagment utility then ran the following in terminal

marc@marc-GA-890GPA-UD3H:~$ sudo mount -t ntfs /dev/sdc /media/1tbdrive
NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
marc@marc-GA-890GPA-UD3H:~$ sudo mount -t ntfs /dev/sdc1 /media/1tbdrive
ntfs_mst_post_read_fixup: magic: 0x129e9206  size: 1024  usa_ofs: 43527  usa_count: 30698: Invalid argument
Record 0 has no FILE magic (0x129e9206)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
marc@marc-GA-890GPA-UD3H:~$ sudo mount /dev/sdc1 /media/1tbdrive
mount: you must specify the filesystem type

:~$ sudo mount /dev/sdc1 /media/1tbdrive
mount: you must specify the filesystem type
marc@marc-GA-890GPA-UD3H:~$ sudo mount -t ntfs /dev/sdc1 /media/1tbdrive
ntfs_mst_post_read_fixup: magic: 0x129e9206  size: 1024  usa_ofs: 43527  usa_count: 30698: Invalid argument
Record 0 has no FILE magic (0x129e9206)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
marc@marc-GA-890GPA-UD3H:~$ sudo mount -t ntfs /dev/sdc1 /media/1tbdrive
ntfs_mst_post_read_fixup: magic: 0x129e9206  size: 1024  usa_ofs: 43527  usa_count: 30698: Invalid argument
Record 0 has no FILE magic (0x129e9206)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by seawolf167 on 2011-06-05
I'll start with this the go back and then look at your terminal output.

Here is the WineHQ article for [Starcraft II]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882"), it may have some comments on SotIS, and the [official bug site ]("http://playsotis.com/index.php?option=com_kunena&func=showcat&catid=15&page=9&Itemid=210")for SotIS.

As for selecting which drive to boot off of, it sounds as if you aren't using GRUB as your MBR entry. If you reinstall GRUB following the steps at [this site]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2"). Then when finished ensure you have the following package 

```
sudo apt-get install os-prober
```

and run the command

```
sudo update-grub
```

to find your Windows installation and add it to the GRUB menu.

---

### Post by seawolf167 on 2011-06-05
Based on the output messages from your second post, it looks like you'll want to run the Windows check disk program. You can do this in Ubuntu as well, but for NTFS read/write support and formatting of drive I suggest using the Windows built-in tools as they seem to work a little better.

You can enter windows, right click "My Computer", then select "Check Disk for Errors" and tick the fix/repair checkboxes.

You can also do this from the Command Prompt or recovery CD via the method suggested of 

```
chkdsk /f C:
```

where C: is the drive letter designation of the disk(s).

Once the drive checks have been completed, boot back into Ubuntu. I suggest trying NTFS-Config first since you have a number of drives/partitions in NTFS. It is easier than manually adding /etc/fstab entries. 

If you have any /etc/fstab entries that you added based on the comments from your first post you should remove those to ensure there are no conflicts.

backup your /etc/fstab file

```
sudo cp /etc/fstab /etc/fstab.backup
```

then remove the entries you manually added

```
sudo gedit /etc/fstab
```

save, then close, then install the programs

```
sudo apt-get install ntfsprogs && sudo apt-get install ntfs-config
```

then run ntfs-config and select your drives you want mounted automatically

[ALT][F2]ntfs-config  to run the program

Here is a [how-to ]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")with pictures for each step.

---

### Post by marcoftheknight on 2011-06-06
I think I figured out what the problem is, which is the following. My Hard drives are formated with Smart File system and linux has trouble reading it. I transfered 75% of all my files to a different hard drive and they showed up, so the plan is to transfer the other 25%. Reformat the hard drive to NTFS file table see if it works. Used windows disk management software to see this will format it in windows. Still have to check the otehr 3 hard drive but they should be easy enough.

FYI I had to unmount on the -->systems-->diskmangement the hard drive and then run the code you gave me for it work for mounting the hard drive thanks again.

Thanks for all the help and code.

---

### Post by seawolf167 on 2011-06-06
Sounds like that will work - hopefully everything will go smoothly!

---

