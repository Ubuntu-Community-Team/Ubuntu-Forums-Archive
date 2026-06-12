---
title: "Drive on ext4 partition does not always mount on startup"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by Newbie2910 on 2011-06-01
I removed all the Windows stuff and consolidated into a large partition, which I then formatted and have set up as a data drive.  Works great, except that it doesn't automatically mount when the machine boots.

If I open Disk Utility I can mount it no problem.  But is there a way to set it up so it always mounts on startup?

---

### Post by garvinrick4 on 2011-06-01
Yes you can mount a partition in fstab (will show you) or you can mount a external at boot
up. I think you have told me formatted ext4 but lets get it all straight. Run this for me in a terminal.
```
sudo fdisk -l
``` (lower case L)
```
sudo parted -l
``` (lower case L)
```
sudo blkid 
``` (lower case L second letter)
#explain which one you want to mount be it a drive or partition and let me know.

---

### Post by Newbie2910 on 2011-06-05
Finally got back to this...

me@Lee:~$ sudo fdisk -l
[sudo] password for me: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00638cbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       27878   223930003+  83  Linux
/dev/sda4           27879       38914    88634369    5  Extended
/dev/sda5           27879       38459    84981760   83  Linux
/dev/sda6           38459       38914     3651584   82  Linux swap / Solaris

Disk /dev/sdc: 8153 MB, 8153726976 bytes
33 heads, 16 sectors/track, 30161 cylinders
Units = cylinders of 528 * 512 = 270336 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30162     7962584    c  W95 FAT32 (LBA)
me@Lee:~$ sudo parted -l
Model: ATA TOSHIBA MK3255GS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  229GB  229GB   primary   ext4
 4      229GB   320GB  90.8GB  extended
 5      229GB   316GB  87.0GB  logical   ext4
 6      316GB   320GB  3739MB  logical   linux-swap(v1)


Model: USB DISK 2.0 (scsi)
Disk /dev/sdc: 8154MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      41.0kB  8154MB  8154MB  primary  fat32        boot, lba


me@Lee:~$ sudo blkid
/dev/sda1: LABEL="Data" UUID="f841f99d-27e3-4476-9c6f-5d95f068acf7" TYPE="ext4" 
/dev/sda5: UUID="32025098-e693-4a24-8c9b-1ccdef5d7911" TYPE="ext4" 
/dev/sda6: UUID="f0392eb1-475e-4b08-8c70-948bf0510576" TYPE="swap" 
/dev/sdc1: LABEL="VAULT" UUID="ECB6-7389" TYPE="vfat" 
me@Lee:~$ 


It's the 229GB partition that I would like to have mount automatically at bootup.

When the machine boots, I can run Disk Utility, select the partition, then click Mount.  It mounts as:
/media/Data  and from then on is fine until I reboot.


thanks.

---

### Post by oldfred on 2011-06-05
Reference data so you can understand details:
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


You can use Data like your label, This is copied from my script where I auto add links from my data to my /home and I use /data as mount. I may have left sudo out on a lot of lines as my script runs as sudo.

mkdir /mnt/data
chown -R $USER:$USER /mnt/data
chmod -R 776 /mnt/data

# modify fstab to mount directory
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# remount from updated fstab
sudo mount -a

fstab entry edited to have your UUID:

# Entry for /dev/sda1 :"
UUID=f841f99d-27e3-4476-9c6f-5d95f068acf7  /mnt/data    ext4         auto,users,rw,relatime               0  2 

Be sure to run the mount -a command as that will tell you if there are any errors. You have to fix errors or revert to backup before rebooting or else you may not be able to reboot.

I have my default folders from /home in my /data as folders of the same name:

I used to do this:
#mv Music oldMusic
#mv Documents oldDocuments
#mv Pictures oldPictures
etc, but now I do it as I install so I know they are empty and just delete them.

I used to link each folder by hand.
#ln -s /mnt/data/Music
#ln -s /mnt/data/Documents
#ln -s /mnt/data/Downloads
etc

But now I link all of them with one command:
# All folders to be linked in /home are in /data as folders
for i in `echo /mnt/data/*`;do ln -s $i; done

Shared /data -see post #4 oldfred
[http://ubuntuforums.org/showthread.p...hlight=%2Fdata]("http://ubuntuforums.org/showthread.p...hlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

