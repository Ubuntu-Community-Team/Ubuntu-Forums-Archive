---
title: "Making an ISO. Where is gone mkisofs?"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by honeybear on 2011-09-02
Hello Ubuntu

Mkisofs is not available any longer.

How to build an ISO file with a given folder? 

```
mkisofs myfolder -o file.iso
```

mkisofs is not available by ubuntu

what is the command to replace it?

---

### Post by femmerlich on 2011-09-02
You can try "genisoimage":

```
sudo apt-get install genisoimage
genisoimage -o filename.iso dirname
```

Hope that helps.

---

### Post by Toz on 2011-09-02
I'm using Natty - **mkisofs** is part of the **genisoimage** package. Install it from the Software Centre. (It's a link to genisoimage).

---

