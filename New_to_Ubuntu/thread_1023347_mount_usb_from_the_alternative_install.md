---
title: "mount usb from the alternative install"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by shaullx on 2008-12-27
im installing the alternative version (8.10) from a usb
but there is a step that the install needs to mount the cd-rom to install from or something like that
anyway there is an option to change the mount manually (currently "/dev/cdrom")
so how to mount the usb instade?
i have 2 hdds both sata
so is it sdb1?

---

### Post by nhasian on 2008-12-27
to see what your drives/partitions are in a terminal type

```
sudo fdisk -l
```

---

### Post by shaullx on 2008-12-28
> **nhasian said:**
> to see what your drives/partitions are in a terminal type

```
sudo fdisk -l
```

but how can i get to the terminal?
it's not live its alternative

---

