---
title: "how to remove a directory"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-05-19
hi,

i want to remove a directory in /usr/bin/   how can i do that in terminal ???
That directory has subdirectories and files as well.

---

### Post by taurus on 2009-05-19
If you remove /usr/bin, you can just kiss your system goodbye since almost all programs are resided in there.  

Any reason why you want to remove /usr/bin?

---

### Post by amac777 on 2009-05-19
To recursevly remove a directory including all files and subdirectories contain within (warning: make sure you don't do this on the wrong directory or you could lose valuable information or destroy your system):

```
rm -r /full/path/to/directory
```

The -r means recursevely delete.

If you don't have permissions to delete the files, you will need to type sudo in front of that command. 

Since a directory inside /usr/bin/ is likely owned by root, you will probably need to use sudo. But be sure you really want to delete the directory and all it's files first because there is no easy way to undo this delete operation.

---

### Post by luckydeveloper on 2009-05-19
> **taurus said:**
> If you remove /usr/bin, you can just kiss your system goodbye since almost all programs are resided in there.  

Any reason why you want to remove /usr/bin?
hahah i know that...

 .. i said.. there is a directory "in" /usr/bin and i want to delete that particular directory alone.

---

### Post by luckydeveloper on 2009-05-19
> **amac777 said:**
> To recursevly remove a directory including all files and subdirectories contain within (warning: make sure you don't do this on the wrong directory or you could lose valuable information or destroy your system):

```
rm -r /full/path/to/directory
```

The -r means recursevely delete.

If you don't have permissions to delete the files, you will need to type sudo in front of that command. 

Since a directory inside /usr/bin/ is likely owned by root, you will probably need to use sudo. But be sure you really want to delete the directory and all it's files first because there is no easy way to undo this delete operation.
thanks..that was what i was looking for.

---

