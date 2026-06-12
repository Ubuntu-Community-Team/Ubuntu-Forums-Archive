---
title: "libexpat.so.0: cannot open shared object file"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by robinpols on 2010-04-27
I am running ubuntu 10.04 64bit. 
for my school i need to use vmware vcenter labmanger wich isnt compatible with the latest version of firefox. So i downloaded the 2.0 version wich is supposed to work. But when i try to install the vmware plugin i get the following error in my terminal:

LoadPlugin: failed to initialize shared library /home/robin/.mozilla/plugins/libmks.so [libexpat.so.0: cannot open shared object file: No such file or directory]

Anyone has suggestions on a workaround for this?

---

### Post by Jon Monreal on 2010-04-27
Try typing the following commands in the terminal one after the other:

```
cd /usr/lib
```
```
ln -s libexpat.so.1 libexpat.so.0
```

And then trying again.

Thanks.

---

