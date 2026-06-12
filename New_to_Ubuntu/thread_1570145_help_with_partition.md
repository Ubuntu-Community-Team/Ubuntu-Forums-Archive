---
title: "help with partition"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-09-07
are there instructions for easily creating a partition on an external usb drive. i have an 8 gb usb drive that i have installed ubuntu on with the pendrivelinux software, and in the past if i try and put a file on the usb drive for storage it does not work. i was thinking a partition is the best way to do this but i have done it wrong in the past.

---

### Post by grief -l on 2010-09-07
you're possibly confusing a partition (a block of cylinders on a storage device) with a file system, the means by which data is logically distributed among those cylinders for easy retrieval.

use GParted to look at your device and tell us how many partitions exist now and what file system they are written to. then we can help.

---

### Post by ornothaloapq on 2010-09-07
the usb is listed as fat 32 and i tried to create a partition earlier that says unallocated.

---

