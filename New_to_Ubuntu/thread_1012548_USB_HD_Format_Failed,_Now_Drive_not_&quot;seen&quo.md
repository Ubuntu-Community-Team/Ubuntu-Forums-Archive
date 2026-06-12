---
title: "USB HD Format Failed, Now Drive not &quot;seen&quot;"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2008-12-15
Anyone,

I am really starting to think this is a hardware error but I am hoping for any help I can get!

I have a 1.8" Toshiba 120gb HD in a case and connect it via USB.  I ran fdisk to format it with the ext2 fs using gparted.  It failed in the middle and now the drive is not recognized by any computer I plug it into.  (Debian, Vista, XP, Ubuntu, OpenSolaris....none)

Is there another way for me to format the drive.  I can hear the drive powering up when I plug the USB in....

I am thinking I shouldn't have bought the cheap drive on EBay :(

Thanks in Advance

---

### Post by bumanie on 2008-12-16
Can post the output of > sudo fdisk -lu with the external unplugged and then the output of sudo fdisk -lu when the drive is plugged into the usb.

---

### Post by J0hnnyBr@v0 on 2008-12-16
Don't be confused, /dev/sdc is a different 120GB HD.  The USB Drive used to show up as /dev/sdd.

In case you don't want to read it all....they look exactly the same....

**_Unplugged:_**
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabacc689

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   478078334   239039136   83  Linux
/dev/sda2       478078335   490223474     6072570    5  Extended
/dev/sda5       478078398   490223474     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3eec3eeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   240107489   120053713+  83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   234436544   117218241    7  HPFS/NTFS

**_Plugged:_**
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabacc689

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   478078334   239039136   83  Linux
/dev/sda2       478078335   490223474     6072570    5  Extended
/dev/sda5       478078398   490223474     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3eec3eeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   240107489   120053713+  83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   234436544   117218241    7  HPFS/NTFS

---

### Post by bumanie on 2008-12-16
Hmmm...it's not recognized at all. May be a cheap drive from e-bay was not a great idea. This is a long shot, but can you post the output of > cat /proc/partitions with the questionable drive plugged in.

---

### Post by J0hnnyBr@v0 on 2008-12-16
Unfortunately that also only shows the original 3 HD's.

I also notice that before the format failed if I booted the PC with the drive plugged in it would recognize it and would pause while it searched the disk for a boot agent.  Now if I boot the PC with the HD plugged in, it does not do this...so it is not being recognized at all.

I personally think the drive is toast, but am trying to exhaust all hope that my $150 is not gone...

When I plug the drive in I can hear and fell the drive spinning up and I get the green light on the USB housing.  Just nothing else is possible after that.

Do you know of any tools, DOS based or other that I can use to try to reformat the drive?  (I assume if the machine can't see the drive at all...then it doesn't really matter...

Thanks in Advance

---

### Post by bumanie on 2008-12-16
Most drive manufacturers have a downloadable tool that will check the drive for errors and fix them if possible. I suspect that this won't help much if the drive cannot be 'seen'. One thing you could try, which again is a bit of a long shot, is to try testdisk and see if it recognizes the drive as sdd. Testdisk is a data/partition recovery tool. It can be installed in ubuntu > sudo apt-get install testdiskand start it with > sudo testdiskHere's the [website]("http://www.cgsecurity.org/wiki/TestDisk") that explains how to use it, also look [here]("http://www.users.bigpond.net.au/hermanzone/p21.html") for further explanation. Good luck, test disk will often recognise partitions that other tools miss - you might be lucky.

---

### Post by J0hnnyBr@v0 on 2008-12-16
OK....I got it viewable again.  I put the HD in my Gigabeat and was able to see the disk so I blew away the partition table with Fdisk.  Well I can see it in Debian, but not Ubuntu....

---

### Post by J0hnnyBr@v0 on 2008-12-16
Disk is now showing up as /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
147 heads, 63 sectors/track, 25314 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234432953   117216476+   b  W95 FAT32

debian:/home/eric# cat /proc/partitions
major minor  #blocks  name

   3     0    8388608 hda
   3     1    7976241 hda1
   3     5     409626 hda5
   8     0  117220824 sda
   8     1  117216476 sda1

debian:/home/eric# fsck -t vfat /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
fsck: fsck.vfat: not found
fsck: Error 2 while executing fsck.vfat for /dev/sda1

debian:/home/eric# dmesg | tail
sda: Current: sense key: No Sense
    Additional sense: No additional sense information
sda: Current: sense key: No Sense
    Additional sense: No additional sense information
sda: Current: sense key: No Sense
    Additional sense: No additional sense information
sda: Current: sense key: No Sense
    Additional sense: No additional sense information
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sda1.

debian:/home/eric# mount -t vfat /dev/sda1 /mnt/harddrive
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Currently running testdisk command on the drive

---

