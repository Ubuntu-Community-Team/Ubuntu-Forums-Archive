---
title: "Installing 10.04, no option to boot linux"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by theubersmurf on 2010-04-30
So I'd configured my HDD in the way I wanted it partitioned, however, Once the installation finishes, I restart, and have no option to select my Linux install. I can only boot to Vista, and I see no option to boot to Ubuntu, I've even gone back to Koala, and am having the same problem. Not sure the problem here. Grub needing to be configured or something?

---

### Post by zipperback on 2010-04-30
Where did you install the GRUB boot loader? If your system is booting directly into Windows and doesn't give the GRUB screen, I'm guessing you didn't install GRUB to be the boot loader.

You should be able to resolve the issue by installing GRUB.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

- zipperback
:popcorn:

---

### Post by garvinrick4 on 2010-04-30
rick@rick-laptop:~$ sudo fdisk -l
[sudo] password for rick: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7e8e0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       15985   128192511    7  HPFS/NTFS
/dev/sda3           15985       36006   160819192+   5  Extended
/dev/sda4           36007       38913    23350477+   7  HPFS/NTFS
/dev/sda5           21349       22807    11719417+  83  Linux
/dev/sda6           15986       17387    11261533+  83  Linux
/dev/sda7           17388       21348    31816701   83  Linux


                                 
[LIST=1]
[*][COLOR=#000080][SIZE=3]**Reinstalling     GRUB 2 from LiveCD**[/SIZE][/COLOR]
If you cannot boot     from GRUB 2 and need to reinstall it, here is the simple method. For     more details or for advanced options, refer to the Ubuntu community     documentation here: [Grub2     - Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"):
[LIST]
[*]Boot the 9.10 Karmic LiveCD to         the Desktop.
[*]Open a terminal - Applications,         Accessories, Terminal.
[*]Determine your normal system         partition - `sudo fdisk -l` (That is a lowercase L)
[*]If you aren't sure, run `df -Th`.         Look for the correct disk size and ext3 or ext4 format.
[*]Mount your normal system         partition:          
         Code:
         sudo mount /dev/sdXY /mnt
[LIST]
[*]Example:             sudo mount /dev/sd*a1* /mnt
[*]Note: The partition to mount is             normally the partition on which Ubuntu was installed: sda1, sdb5,             etc. If you have a separate /boot partition, use the device on             which the /boot partition is located. Grub 2 works best when             installed in the MBR of the drive to which BIOS boots. Also             remember that you *mount* the partition (including the             number) in this step, but you do *not* include the partition             number when you run the "sudo grub-install" command             later.
[*]Note: GRUB 2 counts the first             drive (X) as "0", but the first partition (Y) as "1"
[/LIST]
 
[*]Only if you have a separate boot         partition:
[LIST]
[*]Code:
             sudo mount /dev/sdXY /mnt/boot             with sdXY being your /boot partition designation.
[/LIST]
 
[*]Reinstall GRUB 2:          
         Code:
         sudo grub-install --root-directory=/mnt /dev/sdX
[LIST]
[*]Example:             sudo grub-install --root-directory=/mnt /dev/sd*a*
[*]Note: Substitute the device on             which Ubuntu was installed - sda, sdb, etc. Do *not* specify             a partition number.
[/LIST]
 
[*]Unmount the partition:          
         Code:
         sudo umount /mnt
[*]Reboot.
[/LIST]
 
[/LIST]
 If you look at my fdisk -l  you will see my Code:

 sudo mount  /dev/sda5 /mnt/boot 
 
sudo grub-install --root-directory=/mnt /dev/sda

sudo update-grub

sudo umount /mnt


rick@rick-laptop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext4     12G  3.7G  6.8G  36% /
none      devtmpfs    1.9G  340K  1.9G   1% /dev
none         tmpfs    1.9G  216K  1.9G   1% /dev/shm
none         tmpfs    1.9G  312K  1.9G   1% /var/run
none         tmpfs    1.9G     0  1.9G   0% /var/lock
none         tmpfs    1.9G     0  1.9G   0% /lib/init/rw
/dev/sda7     ext4     30G  8.2G   21G  29% /media/home
rick@rick-laptop:~$

---

