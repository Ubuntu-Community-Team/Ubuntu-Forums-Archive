---
title: "'Autochk' problem when dual booting Ubuntu and Vista"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by shakarchi on 2009-10-03
Hi,

I've tried to install Ubuntu and Vista by partitioning my hard drive. Long story short, Ubuntu is working great (yay) but whenever I try to boot Vista I get a message along the lines of 'autochk program not found' then the BSOD and the computer reboots. I know for a fact that I've screwed up my partitions, to what extent I'm not sure. I've already tried the automatic Vista startup repair tool but unfortunately this didn't work. I also tried to see if the Vista partition was hidden as has been suggested by poking around this forum but again - it is not hidden yet still not working.

I don't know how much help this will be but this is what I get if I type sudo fdisk -l:

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97ba6a9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1698    13631488   27  Unknown
/dev/sda2   *        1698       27809   209738198+  83  Linux
/dev/sda3           27810       38913    89192880    5  Extended
/dev/sda5           27810       37576    78453396   83  Linux
/dev/sda6           37577       38305     5855661   82  Linux swap / Solaris
/dev/sda7           38306       38913     4883728+  83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 253 cylinders
Units = cylinders of 1952 * 2048 = 3997696 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      398636      983425  2283019262   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       86419     1078237  3872056480   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      957932     1949749  3872056384   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1478321     1478349      110998    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```I *think* that my Vista partition is /dev/sda2 but this is labelled as Linux...

And here's what I get in GParted:

[IMG]http://imgur.com/ieTPd.png[/IMG]

I know this is totally my fault for messing around with the partitions but if anyone can help I'll be extremely grateful.

Btw if you haven't noticed I'm still a complete Ubuntu noob so I might need something well explained if it's particularly technical but aside from Ubuntu I'm fairy competent with computers.

Thanks!

---

### Post by shakarchi on 2009-10-04
Apologies for the double post but can anyone help...?

---

