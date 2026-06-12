---
title: "help with dd clone"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by krismx6920 on 2011-01-13
hi i need to clone a flash drive at /dev/sdb to a usb hard drive at /dev/sdb1.  how do i use the dd command?  thanks

---

### Post by wojox on 2011-01-13
```
sudo dd if=/dev/sdb of=/dev/sdb1
```

---

