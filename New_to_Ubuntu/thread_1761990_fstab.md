---
title: "fstab"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by spillage2 on 2011-05-18
Hi,

Really dropped a spanner.

I have edited my fstab file and now cannot boot.

I have tried to edit the file back by booting from a usb drive but do not have the permission do save them.

have tried nautilus but no joy..

any help really would be welcome..

---

### Post by sisco311 on 2011-05-18
> **spillage2 said:**
> 
have tried nautilus but no joy..


Run it as root:
```
gksu nautilus
```

NOTE: Please be careful while running applications with root privileges as you may damage your system.

---

### Post by jethro_tell on 2011-05-18
Try using sudo when you open the fstab.  that should allow you to save on exit.  Also make sure you are editing the fstab on the install not the live disk.

---

### Post by spillage2 on 2011-05-18
Thank you both..

It was one of those panic moments..

I did originally use sudo gedit /fstab once I had cd into the drive cause that wont work then tried gedit fstab instead of sudo gedit fstab....

Thanks again...god damn my /home file...

Spill.

---

