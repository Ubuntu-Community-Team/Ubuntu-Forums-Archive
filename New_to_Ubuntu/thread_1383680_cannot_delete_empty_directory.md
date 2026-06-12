---
title: "cannot delete empty directory"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Matt26 on 2010-01-17
when i try to remove a directory i get the error message:

```
Error removing file: Directory not empty
```

the files in the folder have been deleted but the folder remains.

if i try to remove it using *sudo rm /path/to/folder* i get this:
```
rm: cannot remove `/path/to/folder': Is a directory
```

if i try to remove it using *sudo rmdir /path/to/folder* i get this:

```
rmdir: failed to remove `/path/to/folder': Directory not empty
```

i have also set the ownership of the folder to my username.

any ideas?

---

### Post by gradinaruvasile on 2010-01-17
Go in that folder and do a 

ls -al

see if it returns anything.

Other than that you can remove a folder structure with

rm -rf folder

---

### Post by ajgreeny on 2010-01-17
Maybe some hidden files in the directory that you are unaware of?

---

