---
title: "how to move files from subfolders to the main?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by paker on 2009-08-18
I have a folder with sub, sub-sub, and sub-sub-sub folders. I want to completely eliminate the folder structure and put all files in the main. Is there an easy way to do this? Thanks.

---

### Post by Baneblade on 2009-08-18
Cut and Paste?
Failing that, perhaps a custom script to "mv" the files?

---

### Post by kaibob on 2009-08-18
The following will copy all files from the source directory and subdirectories to the destination directory:

```
find /source/directory -type f -exec cp '{}' /destination/directory ';'
```

You indicate that you want to "put all files in the main." The meaning of this is not clear to me, and its meaning may determine the method used to delete the directory structure.

---

### Post by paker on 2009-08-18
Thank you. That will do. Once files are moved to the main directory from all subdirectories, file conversion operation becomes much easier. Thanks.

---

### Post by paker on 2009-08-19
Thank you. It worked. When I did Right Click > Properties, the destination had 5000 'items' whereas the source had 5100 'items'. I thought some files got dropped. I just didn't know each folder is counted as 'item.' Thanks.

---

### Post by kaibob on 2009-08-19
> **paker said:**
> Thank you. It worked. When I did Right Click > Properties, the destination had 5000 'items' whereas the source had 5100 'items'. I thought some files got dropped. I just didn't know each folder is counted as 'item.' Thanks.
It's possible that files in different subdirectories had identical names and that some copied files overwrote others. The command could be rewritten as a shell script to check for this and to append a number in the case of duplicates. I seem to recall someone doing this as a one-liner, but I can't find it now.

---

