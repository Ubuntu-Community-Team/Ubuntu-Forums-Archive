---
title: "mounting vista ntfs partition"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Dobbick on 2009-08-06
I know I'm probably missing something stupid, but I can't find out what I need anywhere...

I have a Dual boot Vista/Ubuntu through Wubi setup on my laptop.  I want to be able to access the rest of my NTFS formatted hdd where all my music etc is

I'm sure I have to load ntfs-3g or something like that, but I'm at a loss...

Can anyone help?

---

### Post by MelDJ on 2009-08-06
try going to filesystem-host and see whether you can see your windows files there

---

### Post by ptn107 on 2009-08-06
```
sudo mount -t ntfs -o nls=utf8,umask=0222 <device> <dir>
```
ex:
```
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/hdb1 /media/c
```

** <dir> must exist already

[1] [http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

[2] man mount

---

