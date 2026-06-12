---
title: "Drive Disappear in WIndows"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by sportscraz1 on 2009-02-19
Reinstalled Ubuntu yesterday, before that I had a C Drive and D Drive.. C contains Windows, D was empty. I installed Ubuntu from the CD (Boot CD). After the installation the D Drive disappear in Windows. Is that common or a problem? My Hard Drive is 250GB (basically 110GB per drive). 

Beforehand when I loaded ubuntu for the 1st time -2 weeks ago-, was in Windows and afterwards in Windows I was see the D Drive in there. 

Please let me know.

John

---

### Post by taurus on 2009-02-19
Windows can't read ext2/ext3 unless you install a driver for it.  That's why the drive disappeared from windows after you installed Ubuntu on it own partition.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by howefield on 2009-02-19
If you told Ubuntu to use all the space on drive D, then windows will not see it because it cannot read the file format you used, probably ext3 ?

At least not without the help of third party software.

---

