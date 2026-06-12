---
title: "Running the .rar files"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by a_wahab26 on 2011-05-27
Guys can anyone help me out and tell me how to run .rar files on Ubuntu

---

### Post by frankbooth on 2011-05-27
Do you mean extract .rar files?
If so...

**With GUI:**
[img]http://lh6.ggpht.com/jerungkun/R8JJjm1lp4I/AAAAAAAAAj8/rYD3L3aJimw/s800/extract-rar-ubuntu.png[/img]

**In terminal:**
```

cd /to/your/folder/
echo "the command below is only needed if you don't have it installed"
sudo apt-get install unrar 
echo "the next command will extract your rar file in the current directory"
unrar e FILE.rar

```

---

### Post by gandaran on 2011-05-27
> **a_wahab26 said:**
> Guys can anyone help me out and tell me how to run .rar files on Ubuntu
install the rar or unrar packages from software package manager then right click the rar file and choose extract here.

---

### Post by hakermania on 2011-05-27
Explanation: Rar files are compressed files. To uncompress rar files you need to install the "Rar" from the ubuntu software center. Then you will have the ability to compress and uncompress rar files

---

