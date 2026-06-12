---
title: "Make a disk image from folder"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Prince Valiant on 2010-09-14
Hello-

Given a folder with various files copied from a single disk, is it possible to make an .iso disk image?  I'm working off a Acer aspire running Ubuntu 10.04.  

Thanks!

-Val

---

### Post by sisco311 on 2010-09-14
Hi, 

```
genisoimage image.iso path/to/dir
```

or try acetoneiso if you need a GUI application.

---

### Post by Prince Valiant on 2010-09-14
Thanks!

That did the trick.

-Val

---

### Post by HermanAB on 2010-09-14
Howdy,

The older one is mkisofs.

---

