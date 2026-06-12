---
title: "deleted partition boot problem"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by Saeen on 2011-04-22
Hi,
I was trying to go through LFS and to make some space deleted one of my windows partition. Now when i tried to create an ext 4 partition i get the following error:
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=64937263104, size=45000000000, type=0x83
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 13631488000, type 0x27)
new part entry
looking at part 1 (offset 13632536576, size 104857600, type 0x07)
new part entry
looking at part 2 (offset 13738441728, size 486369395712, type 0x05)
Entering MS-DOS extended parser (offset=13738441728, size=486369395712)
readfrom = 13738441728
MSDOS_MAGIC found
readfrom = 116132728320
MSDOS_MAGIC found
readfrom = 167337000960
MSDOS_MAGIC found
readfrom = 171432738816
MSDOS_MAGIC found
readfrom = 64938585600
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
Error: Invalid partition table on /dev/sda -- wrong signature 0.
ped_disk_new() failed


And after a restart i cant go beyond grub> prompt ?
What should i do ?

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       60802   474970113    5  Extended
/dev/sda5            1671        7895    49998848    7  HPFS/NTFS
/dev/sda6           14120       20345    49998848   83  Linux
/dev/sda7           20345       20843     3998720   82  Linux swap / Solaris
/dev/sda8           20843       60802   320970752   83  Linux

---

### Post by Saeen on 2011-04-22
gparted shows i have no partition table..all the hd is unallocated space. even 

though the fdisk -l command output


Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       60802   474970113    5  Extended
/dev/sda5            1671        7895    49998848    7  HPFS/NTFS
/dev/sda6           14120       20345    49998848   83  Linux
/dev/sda7           20345       20843     3998720   82  Linux swap / Solaris
/dev/sda8           20843       60802   320970752   83  Linux[/QUOTE]

Some suggestion ?

---

