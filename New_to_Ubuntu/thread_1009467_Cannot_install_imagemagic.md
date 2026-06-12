---
title: "Cannot install imagemagic"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Mykewl on 2008-12-12
Is this type of problem fixable or will I have to reinstall?
I am using 8.04.
mike@mike-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up imagemagick (7:6.3.7.9.dfsg1-2ubuntu1) ...
Can't read doc-base file `/usr/share/doc-base/imagemagick'
dpkg: error processing imagemagick (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 imagemagick
E: Sub-process /usr/bin/dpkg returned an error code (1)

Note: imagemagick is not in /usr/share/doc-base

---

### Post by Michael.Godawski on 2008-12-13
hi Mykewl, 
try to run these commands, perhaps they will fix the issue or tell us something more.

```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

