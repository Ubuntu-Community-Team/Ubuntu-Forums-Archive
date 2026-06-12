---
title: "mknod fails"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by donescamillo on 2010-09-02
Hi,

In the current directory I have a subdirectory** /devices**
If I write 
**sudo mknod /devices/my_cons** **s 5 1**
bash complains:
**mknod: `/devices/my_cons': No such file or directory**

If I go to devices and run from there:
**cd devices**
**mknod my_cons s 5 1**

it works.

Why does not it work when I specify a path?

---

### Post by Ryadt on 2010-09-02
Try:

```
sudo mknod devices/my_cons s 5 1
```

---

