---
title: "Samba share with write permissions"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by gionnico on 2008-06-30
How can I create some shares that also have write permissions for everyone (no need for password)?

I've got 3 computers and every of these should share 2 folders with each of them. And I also want write permissions.

This shouldn't be so difficult, I've tried lots of options but it didn't work.

---

### Post by superprash2003 on 2008-06-30
you could do that graphically.. just right click on the folder and click on share folder and there uncheck read only.

---

### Post by gionnico on 2008-07-02
It doesn't work, I don't know why.

The guest user is "nobody", as per default.

---

### Post by chessmani on 2008-07-02
I don't know if this piece of advice is good from the point of view of security, but it used to work for me in previous versions: check your fstab. Maybe the partition is mounted as read only.

---

### Post by gionnico on 2008-07-05
No, it is just a folder inside the only (root) partition.

---

