---
title: "new install asks for boot disk upon restart"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by dkwilliams on 2010-11-07
i am a total newbie.  switched from linux mint 7 because of upgrade problems.  finally tried ubuntu, and the install from livecd appeared to work well.  upon restart however, i was then prompted to insert a boot disk.  why am i not booting from my newly installed os?  if this is a grub problem,how do i fix it?  i appreciate any advice.

---

### Post by jtarin on 2010-11-07
It seems to be a Grub problem. Scroll down and try ["METHOD 3 - CHROOT"]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD").

---

### Post by dkwilliams on 2010-11-07
tried what you said.  this was the result.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Unable to seek on /dev/sda


during install i chose to use the entire disk.

---

### Post by oldfred on 2010-11-07
From liveCD run this, but it may also then have issues with drive. 

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by dkwilliams on 2010-11-07
==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1                 512 1,237,988,351 1,237,987,840  83 Linux
/dev/sda2       1,237,988,862 1,250,275,839    12,286,978   5 Extended
Invalid MBR Signature found
/dev/sda5     ? 1,237,988,862 1,237,988,861                   Unknown
/dev/sda6     ? 1,237,988,862 1,237,988,861                   Unknown

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda2

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                isw_raid_member                               
error: /dev/sda2: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6



=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

ERROR: isw: wrong number of devices in RAID set "isw_icjjfdadh_Volume_0000" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_icjjfdadh_Volume_0000" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_icjjfdadh_Volume_0000" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_icjjfdadh_Volume_0000" [1/2] on /dev/sdb
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
ERROR: isw: wrong number of devices in RAID set "isw_icjjfdadh_Volume_0000" [1/2] on /dev/sdb

---

### Post by psusi on 2010-11-07
You appear to have two disks in a broken fake hardware raid.  Were you using a fake raid in the past and no longer are?  You might want to boot the livecd and open the disk utility and check the SMART values on the disks for errors and maybe run the long self test.

---

### Post by dkwilliams on 2010-11-08
i have 640 gb.  pretty sure this is 2 320gb drives. disk utility says i have 2 320gb drives that are good and a 640gb unpartitioned file.  how should i proceed?  formatting the 320gb drives now.

---

### Post by dkwilliams on 2010-11-08
pardon me.  the unpartitioned file is 693mb and not 640gb

---

### Post by psusi on 2010-11-08
The 640 mb one is the cdrom you are booting from.  The other two disk drives appear to have been in a raid at one point, but one of them no longer is.  If you want to use them in a raid then you need to go into the bios utility and delete the broken one and recreate a working one, then install Ubuntu.

---

### Post by oldfred on 2010-11-08
If you do not want RAID you also have to remove meta data from the drives. DO NOT run this if you are fixing your RAID.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

