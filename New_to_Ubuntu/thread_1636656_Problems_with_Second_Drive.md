---
title: "Problems with Second Drive"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by Whisp3r on 2010-12-03
Second Drive Problems
Hi everyone. I'm trying to add a second hard drive to my computer for the purposes of backing up by files before I make the upgrade from 9.04 to 10.10.

I added a second SATA drive, which has become sda. I used gparted and made it FAT32 so my windows OS can use it (rare, but once anda while).

sudo fdisk shows the following:

Code:

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000792f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001    b  W95 FAT32

I did a sudo mount /dev/sda1 /media/drive2, and it shows up under my /media folder. I then sudo mount the drive, it appears on my desk top and I can view it.

I then do the following:
sudo chown -R myusername:myusername /media/drive2, which results in:
Code:

chown: changing ownership of `/media/drive2': Operation not permitted

What am I doing wrong?

---

### Post by oldfred on 2010-12-03
Windows formats FAT nor NTFS support Linux file permissions. If you copy linux data to windows partitions you lose all ownership & permissions. 

You only set a default permission & ownership on windows formats at mounting, you cannot change them.

Do not use FAT unless you have to for your camera, xbox or other device and only for small partitions. It does not have journaling and has a maximum file size of 4GB. It usually does not tell you if you copy a 5GB files and it then is missing the last 1GB.

If you need some compatibility with windows create a separate NTFS partition for that purpose. But for Linux data use ext3 or ext4.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by Whisp3r on 2010-12-03
Thank you very much for your assistance.

---

