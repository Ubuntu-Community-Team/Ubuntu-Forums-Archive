---
title: "Used space on USB key incorrectly reported"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by clbeltz on 2010-06-01
Hello,
I have this nagging issue.  I have an 8GB USB drive, and I use sbackup to create backups.  When I look at the properties for this volume from root, I get the following data:

1) 7.4 GB capacity (formatted ext3)
2) Used: 6.0 GB
3) Contents: 36 items totaling 3.6 GB
4) Free Space: 1.3 GB

So, 1, 2 and 4 make sense together, but I know that there is only 3.6 GB of sbackup files in three folders.  It appears to keep proper track of usage until sbackup deletes old *.ful and *.inc folders.  What needs to be done to fix this?

Loving Lucid otherwise,
Chris

---

### Post by davec64 on 2010-06-02
Hi Chris,

When viewing the contents of the Key in Nautilus, go to **View** and put a tick in **Show Hidden Files**. you may have a trash folder or something else that is normally hidden that has some contents.

If it is the Trash folder, you can remove the rubbish by right clicking **Deleted Items** and selecting **Empty Deleted Items** whilst the key is still connected.

All the best

---

