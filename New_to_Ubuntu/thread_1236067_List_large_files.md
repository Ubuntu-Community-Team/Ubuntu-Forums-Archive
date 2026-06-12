---
title: "List large files"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by lile001 on 2009-08-09
I'm sure there is a handy way to list large files on my system, but I don't know where to start.  

Often I want to clean up the system by listing the largest files above XXX  size, and deciding if I really need to keep them.   Or list all the files recursively and sort by size, starting with the largest.  Or something similar.  

The problem of the moment is, I made an archive of some stuff, but it didnt' end up where I expected it to.  Prolly fatfingered the name or didn't pay attention to the folder or something equally stupid.  It's a big file, so it should stand out among big files in my home folder and subfolders where it is buried.  Another use for a "big file finder".  

--Lawrence

---

### Post by drs305 on 2009-08-09
Here are two commands you can use to find large files. Change the sizes to suit your needs:
```

sudo find / -name '*' -size +1G
or
sudo find / -name '*' -size +500M

```

[_This link_]("http://ubuntuforums.org/showthread.php?t=1122670") will take you to "DiskSpace" where you can investigate what is taking up large amounts of space on your system.

---

### Post by lile001 on 2009-08-09
> **drs305 said:**
> Here are two commands you can use to find large files. Change the sizes to suit your needs:
```

sudo find / -name '*' -size +1G
or
sudo find / -name '*' -size +500M

```The link to "DiskSpace" in my signature line will take you to a guide where you can investigate what is taking up large amounts of space on your system.


Perfect! Thanks!

---

### Post by md2k7 on 2011-05-12
Hi,

sorry for digging this up, but I thought I'd mention a tool I really like for this purpose: JDiskReport. After scanning a whole directory tree, it shows a piechart of disk space usage for folders and sub-folders so you can find your large files and folders quickly.

Yours,
David

---

### Post by andrew.46 on 2011-05-12
Well, since the necroposting has already been done I will join in :). The great use of the linux utility 'find' that has been illustrated here can also be seen in the Ubuntu Community Documentation along with a bunch of other uses:

Ubuntu Community Documentation: find
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

Andrew

---

### Post by geazzy on 2011-05-12
> **drs305 said:**
> Here are two commands you can use to find large files. Change the sizes to suit your needs:
```

sudo find / -name '*' -size +1G
or
sudo find / -name '*' -size +500M

```

The link to "DiskSpace" in my signature line will take you to a guide where you can investigate what is taking up large amounts of space on your system.

thanks for useful command :D

---

### Post by Vaphell on 2011-05-12
-name '*' matches everything anyway so it's not necessary
```
find / -size +1G
``` is enough in this scenario

---

### Post by AllGamer on 2012-07-27
Thanks to all of the above

these 2 commands sure comes in handy when your SSD runs low in space

sudo find / -size +1G
sudo find / -size +500M

:D

---

