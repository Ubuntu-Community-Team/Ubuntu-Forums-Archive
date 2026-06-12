---
title: "System crash, now entire folder is missing from ext2 partition"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by ultralame on 2009-11-12
I had a system crash.  There is a FireWire drive on the system (running 9.04)  That had some photos that were not backed up yet.

That portion of the disk seems tho have disappeared.  That is, a lower-level directory is no longer listed, and all the files in that folder (some of which are the ones that are not backed up) are missing.

Is there a tool for finding these lost folders/files?

---

### Post by cariboo on 2009-11-12
I would suggest running fsck on the partition to see if that solves the problem. If it doesn't, [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") is in the repositories, a part of the package is photorec. which should be able to retrieve your missing photos.

---

