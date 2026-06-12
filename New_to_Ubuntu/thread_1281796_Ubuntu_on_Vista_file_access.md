---
title: "Ubuntu on Vista file access"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by s-geek on 2009-10-03
Hi... I installed Ubuntu 8.04 yesterday as an application on Vista but when I run Ubuntu i cant access my files on the harddrive on vista. I ran the ntfs configuration tool and still nothing. Maybe i'm looking in the wrong place... i have been checking under file system. Any help please... i am trying to avoid partitioning my hard drive.

---

### Post by privatejarhead on 2009-10-03
im having the same problems as well with a wubi install. maybe if you were to do a full dual-boot install with ubuntu, then you could access your vista files. i would do that, but im waiting for windows 7/ubuntu 9.10 to come out in a few weeks.

---

### Post by pedro3005 on 2009-10-03
It won't be under File System. Try opening nautilus (the file manager) and type computer:/// at the bar. It will be like Window's "My Computer".

---

### Post by BinaryFeast on 2009-10-03
All your Vista files and folders are under /host.
So for instance you can type:

```
nautilus /host
```

and you will see some familiar stuff.

---

### Post by s-geek on 2009-10-04
Thanks binary feast, that worked like a charm.

---

### Post by nhasian on 2009-10-04
correct me if i'm wrong, but isnt the /Host directory a bookmark you can access from the Places Menu?  If not you can easily make it a bookmark by right clicking on it and choosing bookmark from the Nautilus file manager.

---

