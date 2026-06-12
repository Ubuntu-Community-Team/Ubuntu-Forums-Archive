---
title: "How to remove an empty file"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by phil66 on 2010-05-15
Lucid 10.04
Gnome
Grub 2
Compiz

I have a couple of files in /etc/grub.d that were made by mistake.
I want to remove them but the apt-get --remove command just returns a file not found prompt.

I was able to change ownership of the file with chown
I can find the file manually from file system

What am I missing that I cannot remove this file.

---

### Post by drs305 on 2010-05-15
```
gksu nautilus /etc/grub.d/
```
Enter your password and you will have a file browser open with admin rights. You can delete any file you wish, so be sure you are deleting the correct file(s). Use SHIFT-DEL if you don't want them to end up in root's trash bin.

---

### Post by MuH4hA on 2010-05-15
the command to remove a file is ```
$rm /path/to/file
``` - not apt-get. APT is the package management system...

---

### Post by phil66 on 2010-05-15
> **drs305 said:**
> ```
gksu nautilus /etc/grub.d/
```
Enter your password and you will have a file browser open with admin rights. You can delete any file you wish, so be sure you are deleting the correct file(s). Use SHIFT-DEL if you don't want them to end up in root's trash bin.

Thanks that worked just fine

---

