---
title: "Hard links shown in ls -l doesn't make sense!"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by john77eipe on 2010-12-03
Hi again,

I have a folder "temp" and 2 files, one inside temp and another outside but pointing to the same file.

The file names are t and tlink.


eipe@eipe-john:~$ ls -l
-rw-r--r--  2 eipe eipe    6 2010-12-03 14:39 t
drwxr-xr-x  2 eipe eipe 4096 2010-12-03 15:55 temp

eipe@eipe-john:~/temp$ ls -la
drwxr-xr-x  2 eipe eipe 4096 2010-12-03 15:55 .
drwxr-xr-x 48 eipe eipe 4096 2010-12-03 15:54 ..
-rw-r--r--  2 eipe eipe    6 2010-12-03 14:39 tlink

1. I understand that the second column shows the hard link count for files. But what does it show for directories like temp? It shows 2 even after deleting tlink.

2. For the pointer .. it shows 48! what does it mean? Also .. are pointers, right?

---

### Post by rampageoberon on 2010-12-03
> **john77eipe said:**
> 
1. I understand that the second column shows the hard link count for files. But what does it show for directories like temp? It shows 2 even after deleting tlink.

The second column is the count of the number of subdirectories, if it is a directory. If it is a file, then it will be 1.

An empty directory will read as 2. And having a file tlink in the temp directory doesn't change this.

The 48 means you have 46 + (. and ..) directories in your home folder.

Hope this helps.

---

### Post by mcduck on 2010-12-03
the "." and ".." are files (or actually links) as well. "." links to current directory and ".." to parent directory.

So even "empty" directory will always have these two files in it.

---

### Post by TeoBigusGeekus on 2010-12-03
[http://docweb.cns.ufl.edu/docs/d0107/ar07s04.html]("http://docweb.cns.ufl.edu/docs/d0107/ar07s04.html")

---

### Post by john77eipe on 2010-12-03
thanks a ton guys! I got it.

---

