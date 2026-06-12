---
title: "How do I remove GTK+-2.12.12 by command line"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-08-13
Hi,

I have currently have 2 versions of GTK+, 2.12.12 and 2.20.1 How do I remove the version of gtk+-2.12.12, since when I installing another package(i.e glade), it is pointing at 2.12.12..BTW, i need it to point to the 2.20.1 version, instead..I try to "sudo apt-get remove " but I cannot find it. Also, both 2 packages were installed via source, not synaptic manager..

Thanks in advance.

-alfa-

---

### Post by TeoBigusGeekus on 2011-08-13
You have to find the source files again and compile them, but instead of
```
sudo make install
```
you must give
```
sudo make uninstall
```

---

### Post by alfa_80 on 2011-08-13
> **TeoBigusGeekus said:**
> You have to find the source files again and compile them, but instead of
```
sudo make install
```you must give
```
sudo make uninstall
```


The problem is that the directory of GTK+-2.12.12 has been deleted. Any idea?

---

### Post by TeoBigusGeekus on 2011-08-13
Install it again and then try to uninstall it.

---

