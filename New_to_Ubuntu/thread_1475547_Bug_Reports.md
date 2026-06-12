---
title: "Bug Reports?"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by McRat on 2010-05-07
Where do we submit these?

Installed 10.04 LTS 64bit Server on a new AMD64 Clone box.  Set up to use 100gb of a Western Digital SATA 320gb drive, and turned on encrypt, LVM2?  No other O/Ss, clean HDD.  (I reserved 2/3 of the drive for future use).  Only one HDD and one DVD/CD is installed, using mobo's SATA connections.  Gigabyte MA785 mobo.

System works fine right now, but Disk Utility reports:

Peripheral Devices:
   320gb, dev/mapper/sda5_crypt, no partitions, no usage, no type.

   101gb, dev/mapper/ubuntu64-root, no partitions, mounted, EXT4.

   4.3gb, dev/mapper/ubuntu64-swap_1, no partitions, no usage, no type.

When I did a "properties" on the drive, it reported 128 TB in size, and kept counting past 200,000 files on a new install before I quit.  It reports 85gb available. Computer:/// Volume: Unknown. 

Disk Usage Analyzer = 93gb avail, 3gb used, this is perhaps correct for that first partition.  

This info was through the GUI, I still sucketh at commandish.

Seems since I didn't allocate the entire drive during setup, it got confused.  When I did a i86 32bit install, full drive size, everything AOK.

I don't think it's anything but a reporting error, but I'm going to reinstall, this time using the whole drive.

---

### Post by cak3 on 2010-05-07
Ubuntu bugs are usually filed in Launchpad. you can use apport to file the bug and automatically attach relevant data.

the short version is you can report a bug by running
```

ubuntu-bug [packagename]

```
in terminal.

see [http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs) for an in-depth guide and more information.

---

