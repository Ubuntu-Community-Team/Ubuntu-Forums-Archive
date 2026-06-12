---
title: "Which Partition Is Windows On?"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-07-23
I installed Windows 7 after I had installed mint and then I repaired the grub bootloader however to add Windows 7 to the boot-screen I need to know what partition it's installed on...how do I find this out?

---

### Post by c0mput3r_n3rD on 2009-07-23
You can install a Parition Editor from add/remove that will list your partitions and informations about them (include name).

---

### Post by LewRockwell on 2009-07-23
```
sudo fdisk -l
```

that's a little "L" and not a one...btw...

.

---

### Post by kamitsukai on 2009-07-23
> **LewRockwell said:**
> ```
sudo fdisk -l
```that's a little "L" and not a one...btw...

.

thanks =]

---

