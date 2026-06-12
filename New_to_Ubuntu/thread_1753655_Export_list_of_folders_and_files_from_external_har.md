---
title: "Export list of folders and files from external hard drive"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by motorcity909 on 2011-05-09
Hi all

I've got an external hard-drive which shows as /media/FREECOM HDD

Is there a command to list all the folders, subfolders and files on that hard drive into a text file?

Many thanks
Dave

---

### Post by nothingspecial on 2011-05-09
> **motorcity909 said:**
> Hi all

I've got an external hard-drive which shows as /media/FREECOM HDD

Is there a command to list all the folders, subfolders and files on that hard drive into a text file?

Many thanks
Dave

Yep 

```
ls -R /media/FREECOM\ HDD/ > filelist.txt
```

That will make a text file named filelist.txt

---

### Post by motorcity909 on 2011-05-09
That's great, worked brilliantly.

Many thanks
Dave

---

