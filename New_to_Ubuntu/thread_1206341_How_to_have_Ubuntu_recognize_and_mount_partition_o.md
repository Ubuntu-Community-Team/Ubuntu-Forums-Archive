---
title: "How to have Ubuntu recognize and mount partition on internal drive"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Wilbur Kelly on 2009-07-07
I have a single hard drive.  I have Ubuntu 8.10 and it is uptodate. I want to use remastersys to backup the system before I update to 9.4.  Remastersys has a limit that is exceeded by the size of my document file.  I have a partition that is not recognized by my installation that has plenty of room to move my documents to.  I have tried to modify my /etc/fstab to allow the partition to be seen but I don't understand how to add what I need to in order to have ubuntu mount the partition.  (I do know how to find the UUID of /dev/sda3 from Gparted.)

This is the current fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=378110a8-daba-449b-b6a5-6dad2c25f010 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=47926625-c32e-430a-8465-14dbf397845a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

The fdisk -l is:
wkelly@wkelly-desktop:~$ sudo fdisk -l
[sudo] password for wkelly: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3cf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17847   143355996   83  Linux
/dev/sda2           38183       38913     5871757+   5  Extended
/dev/sda3           17848       35694   143356027+  83  Linux
/dev/sda5           38183       38913     5871726   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc703da80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2      121601   976752000    5  Extended
/dev/sdb5               2      121601   976751968+   7  HPFS/NTFS
wkelly@wkelly-desktop:~$ 

Using Gparted:
partition                 Filesystem      Size
/dev/mapper/_dev_sda3ql   reiserfs        136.71 GB
/dev/sda
  /dev/sda1               ext3            136.71 GB 
  /dev/sda3               ext3            136.71 GB
uaallocated                                19.06 GB
  /dev/sda2               extended          5.60 GB
  /dev/sda5               linux-swap        5.60 GB

Note: /dev/sda1 is the /mountpoint and the boot partition

I set things up a long time ago and think the boot partition which has only 5.65 GBs points to and loads the encrypted partition:
 /dev/mapper/_dev_sda3ql   reiserfs        136.71 GB
which is /home

I didn't know what I was doing when I set this up this way but followed the instructions of an article that suggested 1) a separate home patition was good and 2) an encrypted home partition was better and here is how to set up an encrypted separate home partition.  It has worked without any trouble ever since.

So, my problem (I think) is how to set things up right in /etc/fstab so I can mount the unused area of either /dev/sda1 or the totally unused partition /dev/sda3 (or both)

I have tried to look for instructions to modify fstab but the several things I have tried didn't work.

TIA
wkelly

Added after posting the above by "edit":

The following information may be of some use in looking at the question:

wkelly@wkelly-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-07-07 00:20 378110a8-daba-449b-b6a5-6dad2c25f010 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-07-07 00:20 47926625-c32e-430a-8465-14dbf397845a -> ../../sda5
lrwxrwxrwx 1 root root 22 2009-07-07 00:22 5288bbe5-d21a-416d-8d6e-a8f9c09a38bc -> ../../mapper/_dev_sda3
lrwxrwxrwx 1 root root 10 2009-07-07 00:20 A97B4C831B6BE655 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2009-07-07 00:20 be0e63a4-a275-4558-a15a-4a4ea2bd5103 -> ../../sda3

wkelly@wkelly-desktop:~$ sudo vol_id /dev/sda3
[sudo] password for wkelly: 
ID_FS_USAGE=crypto
ID_FS_TYPE=crypto_LUKS
ID_FS_VERSION=2
ID_FS_UUID=be0e63a4-a275-4558-a15a-4a4ea2bd5103
ID_FS_UUID_ENC=be0e63a4-a275-4558-a15a-4a4ea2bd5103
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
wkelly@wkelly-desktop:~$ 

Of interest in the above is the fact that the first section, ls -l /dev/disk/by-uuid, yields a UUID for everything BUT /dev/sda3 though Gparted lists the UUID for /dev/sda3  Does that mean that the /mapper/_dev_sda3 is preventing /dev/sda3 from being seen somehow because both are called sda3?  That appears to be what the second inquiry: sudo vol_id /dev/sda3 implys?  If this is so how do I fix it?
Gparted says the UUID for /dev/sda3 is:UUID=37101111-2f4b-434f-999d-542a0986b5df

---

### Post by frunns on 2009-07-07
I seriously do not like fstab. My suggestion is that you install pysdm, a neat little GUI for fstab. Here's an article on the subject
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)
Be sure to back fstab up first. Good luck!

---

### Post by Wilbur Kelly on 2009-07-07
Thanks, I'll install it and give it a try, but it's late tonight and work comes early so it may be tomorrow night before I can try it... Thanks

---

### Post by Wilbur Kelly on 2009-07-08
Well, I did install PySDM but it is not responding as expected.  It sees the one hard drive I have: sda but when I click on it, the right side of the panel remains grayed out, and I see no triangle on the left (mentioned below):

"Select the partition which you want to mount by expanding the drive (sda, sdb, etc) and clicking on the triangle to the left of the individual partition (sda, sdb, etc). Until you select a partition the right side of PySDM will be grayed out and unavailable for input. If you don't know which partition you want to select, go to the Which Partition? section at the bottom of this page for help. The first time PySDM works with a partition, even if an entry already exists in fstab, it will ask 'Configure Now? - click OK. " 

There is no way to get the right side of PySDM to ungrey and there is no 'configure now? - click OK'

I can plugin an external drive and PySDM recognizes it, it has a triangle, and PsSDM ungreys out the right panel and gives me the opportunity to use the right panel choices.  It is not giving me the opportunity to use the program on the internal drive: there is only one and it is not letting me see the partions that are clearly shown with Gparted and with: sudo fdisk -l

I'd be happy to use it if I could.  I am open to suggestions.  There has to be some pretty simple line to add to Fstab or which will allow me to use PySDM.

TIA
wk

OK: editing:
I think my problem is that the encrypted home partition is done with /dev/mapper/_dev_sda3 is preventing Gparted from seeing /dev/sda3 somehow.  In Gparted I have key symbols in front of the filesystem names except for /dev/sda3 which has a yellow triangel with an exclamation mark in it.  When I googled /dev/mapper I got: "The Linux Logical Volume Manager (LVM) is a mechanism for virtualizing disks." and since both end in sda3.  When I try to edit fstab and use UUID for the partition I obtain from Gparted it doesn't recognize the drive:

frp, sudo nano /etc/fstab I now have:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults$
# /dev/sda1
UUID=378110a8-daba-449b-b6a5-6dad2c25f010  /              ext3         relatime$
# /dev/sda5
UUID=47926625-c32e-430a-8465-14dbf397845a  none           swap         sw      $
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noa$

/dev/sdb5                                  /media/sdb5    ntfs         defaults$
# /dev/sda3
UUID=37101111-2f4b-434f-999d-542a0986b5df /storage ext3 defaults 0 0

 but when I try to mount -a I get:
wkelly@wkelly-desktop:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/37101111-2f4b-434f-999d-542a0986b5df does not exist

It exists but Gparted has a problem with it, hence the yellow triangle with the exclamation point.  And LVM must be the etiology since it is naming the virtual volume.  So... how to manipulate the names or the assignment of names to prevent the confusion...?
TIA,
wk
Oops... when I tried a lvm command, vgchange, my system informed me that the program was not installed and then told me how to install lvm2 package.  So I guess I don't understand yet how the encrypted volume got the same ending sda3 as the unused partition sda3...

I am gettin dizzy looking at this.  Any suggestions ....

---

