---
title: "How to access other filesystems in terminal?"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by cacs on 2011-05-12
Hi there.

I would like to access other file system than default file system (eg a removable disk) on a terminal window...

I change to "/" but the removable disks seams not to exist...

How to access them?

Thanks.

---

### Post by Bapun007 on 2011-05-12
> **cacs said:**
> Hi there.

I would like to access other file system than default file system (eg a removable disk) on a terminal window...

I change to "/" but the removable disks seams not to exist...

How to access them?

Thanks.

all removable disks are mounted automatically on ubuntu . For access them you have to go to mount directory under root by cd command .

cd /mount

---

### Post by frankbooth on 2011-05-12
You should be able to find all your mounted devices by typing:

```
cd /media/
```

followed by (to list the drives):

```
ls
```

then type: ```
cd NAMEOFYOURDRIVE
``` to enter the desired device

---

### Post by cacs on 2011-05-12
Thank you, Bapun007 and frankbooth.
The filesystems are mounted in "/media/"! There's just what i needed to know! :P
C.S.

---

