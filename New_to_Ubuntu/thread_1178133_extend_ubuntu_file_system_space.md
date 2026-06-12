---
title: "extend ubuntu file system space"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by alexeyhurricane on 2009-06-04
i installed ubuntu on vista ultimate  and want to update ubuntu but it says not enough space but i got about 100gbs free. so the question is how can i extend the ubuntu space?

---

### Post by nandemonai on 2009-06-04
This is a Wubi install that you did from inside Windows?

---

### Post by alexeyhurricane on 2009-06-04
what do u mean by wubi > if on they disk start up it is said wubi something possibly it is wubi , i downloaded ubuntu 9.04 , 64 bit

---

### Post by nandemonai on 2009-06-04
A wubi install is when you install Ubuntu from the disk while inside of Windows, rather than actually booting from the Live CD.

Assuming this is a wubi install (which it sounds like) then I think you can use LVPM to resize as it's not a real partition but a virtual disk file that resides on your Windows disk.

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

It would likely be easier to actually backup your /home/ directory and uninstall/reinstall Ubuntu from Add/Remove in Windows but this time give it a larger chunk of the disk. Something above say 10G depending on how much software and data you wish you wish to store in Ubuntu.

Personally I'd recommend a REAL install over a wubi install though.

---

### Post by alexeyhurricane on 2009-06-04
how to delete ubuntu then?

---

### Post by alexeyhurricane on 2009-06-04
so i should choose manual install ill try to do that!

---

