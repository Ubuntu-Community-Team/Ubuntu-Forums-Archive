---
title: "Extend Ubuntu 10.10 partition"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by gamepoint on 2010-10-19
recently, I decided to give ubuntu a try, So, i select only 10g for the ubuntu partition.After that, i found that ubuntu is very good and i decided to extend my partition to 40-50 g without reformatting:)..is that possible?

my ubuntu was installed separated from windows.My windows is in C..ubuntu is in L partition.Please help?

---

### Post by Elfy on 2010-10-19
Yes it is possible.

If you installed with wubi - [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

If you installed with a normal dual boot - [http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html) and [http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

There are hundreds of extending partition threads on here - try searching in googlubuntu [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by Mark Phelps on 2010-10-19
> **gamepoint said:**
> My windows is in C..ubuntu is in L partition.Please help?

AFAIK, the only way that an Ubuntu install gets assigned a drive "letter" is if you install via Wubi -- so make sure you follow THOSE directions to change the allocation.

---

