---
title: "Is there any way to expand all folders in a directory?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by hopelessone on 2009-03-22
Hi,

In 1 folder i have 2,000 Folders (with other folders inside of them)and i would like to put all the files in 1 folder.

Is it possible to do this? can i expand them all somehow?

Thanks..

---

### Post by llamabr on 2009-03-22
You need a regular expression.  Welcome to the strength of the command line.

What are the folders called?

---

### Post by ajgreeny on 2009-03-22
If there are not too many levels you can move all the files with mv or copy with cp, but if there are lots of levels it may be more difficult and require more separate commands, as subfolders will also be moved/copied if you try to do it recursively as far as I can see, and you may end up with a bit of a mess.

No doubt others will be able to tell you how to do it just for files but not also moving the subfolders.

---

### Post by sisco311 on 2009-03-22
you can use the find command.

to copy all the files from /path/to/dir and its subdirectories to /path/to/dest :
```
find /path/to/dir -type f -exec cp --backup=numbered {} /path/to/dest \;
```

to move the files:
```
find /path/to/dir -type f -exec mv --backup=numbered {} /path/to/dest \;
```

!!! /path/to/dest is NOT a subdirectory of /path/to/dir.

---

