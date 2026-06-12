---
title: "Using ddrescue and limiting the dump to /"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-02-09
I want to backup the entire OS, if possible, using ddrescue. My /sda is a 400 gig drive, on which there is:


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          12       96358+   7  HPFS/NTFS
/dev/sdb2              13        4462    35736576    7  HPFS/NTFS
/dev/sdb3            6503       48641   338481517+   5  Extended
/dev/sdb4   *        4463        6502    16386300   83  Linux
/dev/sdb5            7983       47621   318400267+  83  Linux
/dev/sdb6           47622       48641     8193118+  82  Linux swap / Solaris

As my backup drive (external via USB) is only 300 gig, I want to know how to use ddrescue to back up all of the partitions, but only that portion of /sdb3 that is in use. /sdb3 is my /home.

Lastly, the entire size-in-use of the /sda is smaller than the external 300 gig drive.

---

