---
title: "Windows access to drives"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Dookert on 2009-12-13
Hey all,

trying to get my network setup proper, the way I want it. Im a noob.

What I wanna do is share /dev/sdb2 with a windows 7 machine on the network. Currently windows has access to the /home directory of /dev/sdb1 . I can see the drive(sdb2) in windows. In ubuntu I used nautilus to navigate back into media and then selected sdb2 (named New Volume) for sharing and read write access. However, in windows, I get a "no access...contact network administartor..." message, which makes me think the problem is on the ubuntu machines end?
  
 Heres my drives:

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed56ed56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2            8925       19451    84558127+   f  W95 Ext'd (LBA)
/dev/sda5            8925       19451    84558096    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedacedac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8510    68356543+  83  Linux
/dev/sdb2            8511       18236    78124095    7  HPFS/NTFS
/dev/sdb3           18237       19457     9807682+   5  Extended
/dev/sdb5           18237       19457     9807651   82  Linux swap / Solaris

Disk /dev/sdd: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         123      987104    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)

```

what should I do?

---

### Post by Dookert on 2009-12-14
nobodies got any ideas eh? still cant get this to work

---

### Post by longtom on 2009-12-14
Some time ago I connected to a windows network.  This are the tips I got from the community:

1, Create a workgroup in windows and share some folders!
2, Install Samba in ubuntu from synaptic!
3, I like to reboot here!
3, open run dialogue by pressing ALT and F2
4,Type 
```
shares-admin 
```

5, unlock with your password!
6, Select the folders you would share!
7, nearly there, click the second tab "General Properties"and enter the workgroup name!

Congrats you should be up and running

---

