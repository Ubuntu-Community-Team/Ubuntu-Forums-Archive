---
title: "Problem deleting file from Pen Drive"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Linux Lover on 2009-01-28
My friend has given me a pen drive which contains some windows virus. There is a folder named "recycler" and two files outside the folder 'explorer.exe' and 'isetup.exe'. I am trying to remove all the things by using mkfs, and the output is as follows:

```
linuxlover@linuxlover-desktop:~$ sudo umount /dev/sdb
linuxlover@linuxlover-desktop:~$ sudo mkfs.ext3 /dev/sdb
mke2fs 1.40.2 (12-Jul-2007)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
246784 inodes, 493567 blocks
24678 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=507510784
16 block groups
32768 blocks per group, 32768 fragments per group
15424 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912

Writing inode tables: done
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 20 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
linuxlover@linuxlover-desktop:~$ sudo e2label /dev/sdb usb-pen
e2label: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock.
linuxlover@linuxlover-desktop:~$        
```
How to format the disc so that nothing appears again? I am a newbie, please help me with detailed command I should use. Thanks in advance.

---

### Post by kpkeerthi on 2009-01-28
Try deleting the existing partion(s) and then create a new partion.
[http://blog.dotkam.com/2008/07/10/restoreformat-usb-flash-drive/](http://blog.dotkam.com/2008/07/10/restoreformat-usb-flash-drive/)

---

### Post by clive littlewood on 2009-01-28
Hi

Just use Gparted System > Admin > Partition editor and reformat the Drive.

If Gparted is not installed then use it from the live CD or install from Synaptic.

Hope this helps         :D

Clive

---

### Post by Linux Lover on 2009-01-28
First thank you for your response. I am now stunned... just see the result
```

linuxlover@linuxlover-desktop:~$ sudo fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 2021 MB, 2021654016 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      199216      491461   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(199215, 34, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(491460, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       43188      538843   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(43187, 17, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(538842, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      478721      974376   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(478720, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(974375, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      738782      738796       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(738781, 41, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(738795, 54, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Command (m for help): d
Partition number (1-4): 1

Command (m for help): d
Partition number (1-4): 2

Command (m for help): d
Partition number (1-4): 3

Command (m for help): d
Selected partition 4

Command (m for help): p

Disk /dev/sdb: 2021 MB, 2021654016 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6f20736b

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1010, default 1):
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-1010, default 1010):
Using default value 1010

Command (m for help): p

Disk /dev/sdb: 2021 MB, 2021654016 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6f20736b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1010     1972499   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 0: Success.
The kernel still uses the old table.
The new table will be used at the next reboot.

Error closing file
linuxlover@linuxlover-desktop:~$  
```

Fdisk even failed. Don't know the reason, am I missing something?

---

### Post by Efros on 2009-01-28
Sounds like its FUBARred.

---

