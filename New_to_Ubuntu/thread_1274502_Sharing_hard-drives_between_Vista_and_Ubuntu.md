---
title: "Sharing hard-drives between Vista and Ubuntu"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by ChoatJor on 2009-09-24
I just installed Ubuntu onto an external hard drive. When I boot into Vista I can't access the files on the external hard drive, and when I boot into Ubuntu, I can't access the files from the original hard drive. Is there a way to merge these two systems so that through both OS's I can access all files. Thank in advance.

---

### Post by Xero Xenith on 2009-09-24
Assuming the external drive partition is ext2, ext3 or ext4, [ext2ifs]("http://www.fs-driver.org/") can be used to access it on Vista.

Why the Vista drive isn't working on Ubuntu, however, is more of a mystery...

---

### Post by Darkwing-Duck on 2009-09-24
What version of Ubuntu are you running?

---

### Post by wobin77 on 2009-09-24
Did you mount the vista drives?

---

### Post by ChoatJor on 2009-09-24
Thanks for all the replies. It's version 9.04.

---

### Post by ChoatJor on 2009-09-24
Thanks a lot to Xero. I'm able to access it now.

---

