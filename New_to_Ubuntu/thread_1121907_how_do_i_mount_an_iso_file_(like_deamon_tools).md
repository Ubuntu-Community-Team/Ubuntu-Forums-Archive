---
title: "how do i mount an iso file (like deamon tools)"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by y_garti on 2009-04-10
hi
is anybody know a way that I can mount an iso file
in windows i use a program call DAEMON Tools but i don't know how to do this in ubuntu

---

### Post by binbash on 2009-04-10
sudo mkdir /mnt/iso
sudo mount -o loop /home/asdasd/sdada/yourisoname.iso /mnt/iso

---

### Post by CatKiller on 2009-04-10
[https://wiki.ubuntu.com/MountIso](https://wiki.ubuntu.com/MountIso)

---

### Post by iponeverything on 2009-04-10
```
sudo mount -o loop name_of_file.iso /mnt

```

---

### Post by iponeverything on 2009-04-10
wow.. three replies in 1 minute ;)

---

### Post by y_garti on 2009-04-10
wow i didn't know that it was that easy thanks allot

---

