---
title: "deleting rights"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2009-08-23
i have mounted a NAS drive in Ubuntu with the following line in my fstab file
```
//192.168.1.41/public /media/public/ cifs nounix,username=xxx,password=xxx,file_mode=0777,dir_mode=0777 0 0
```
The problem I have is that I can only delete individual files or individual folders but only when they are empty. When I try to do so I get this error: > Error removing file: No such file or directory
Can someone see what how I can change my fstab file so that I can have the rights to delete folder(s) and files as I do my local drive?
Thanks

---

### Post by Penguin Guy on 2009-08-23
> **steinzeitmensch said:**
> Error removing file: No such file or directory.
I don't think this is a permission problem.

---

