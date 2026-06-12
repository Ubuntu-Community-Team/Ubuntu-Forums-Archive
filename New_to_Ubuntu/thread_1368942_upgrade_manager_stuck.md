---
title: "upgrade manager stuck"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Rowanmf on 2009-12-31
Hi everyone , happy new year to you all , please can someone help , before i left work for the holidays upgrade manager downloaded all the new updates , including the new linux kernel -linux-image-2.6.31-16-generic , unfortunatly it seems the download was not great and it is now sitting in my upgrade manager constantly asking to install the kernel but it fails with the following error -E: /var/cache/apt/archives/linux-image-2.6.31-16-generic_2.6.31-16.53_i386.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.31-16-generic/kernel/drivers/mtd/ubi/ubi.ko')

How can i get rid of this failing package so that it can be re downloaded later ...

Thanks

Rowan
plse help ..
plse help ..

---

### Post by Rowanmf on 2009-12-31
plse plse help ...

---

### Post by Rowanmf on 2010-01-01
plse plse help ....

---

### Post by mechro on 2010-01-01
Try **gksudo nautilus**... navigate to and delete /var/cache/apt/archives/linux-image-2.6.31-16-generic_2.6.31-16.53_i386.deb

Restart **System > Admin... > Update Manager** and **Check**.

---

### Post by kansasnoob on 2010-01-01
Possibly just run from terminal;

```
sudo apt-get clean
```

---

### Post by Rowanmf on 2010-01-02
many thanks for the help , i had tried browsing but not using sudo option was what was stopping me from clearing the files out , thanks for the help ...

Rowan

---

