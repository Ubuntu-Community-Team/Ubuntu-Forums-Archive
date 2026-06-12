---
title: "rsync and exclude-from help"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by vbmark on 2010-05-01
Hello,

My script is:```
#!/bin/bash
rm '/home/mark/Scripts/Backup/backuplog.txt'
opts="-r -t -v --progress --delete --ignore-existing"
backuplog="backuplog.txt"

rsync $opts --exclude-from /home/mark/Scripts/Backup/exclude.txt /home/ /media/111GB/Ubuntu/home/ >> $backuplog
```My exclude.txt is:```
mark/.macromedia/*
mark/.mozilla/*
```Now matter what I try, those two folders alway are copied.
What am I doing wrong?

Thanks!
Mark

---

### Post by jvc26 on 2010-05-04
Have you tried with full paths rather than relative paths in the exclude.txt?

J

---

### Post by vbmark on 2010-05-04
Hi jvc26,

Thanks for responding to my post.  I finally figured it out.  I had to add the - (dash) before each line in my exclude.txt.

Thanks!
Mark

---

