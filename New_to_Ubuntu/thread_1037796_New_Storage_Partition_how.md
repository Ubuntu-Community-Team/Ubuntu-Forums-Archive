---
title: "New Storage Partition how?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-01-12
I would like to create a 400 GiB storage partition on my harddrive but can get it to work. First is even a 400 GiB partition recommended with file system Ext3? I used GParted to create the partition but when I try to copy files to the storage partition does it say that I don't have the necessary right, can this be changed? atm can only root write to the storage partition.

---

### Post by cjv8888 on 2009-01-12
you can try to change owner to yourself

```
sudo chown -R username: /path/to/partition
```

---

### Post by meindian523 on 2009-01-12
or edit /etc/fstab with ```
gksudo gedit /etc/fstab
``` and add ```
user
``` to the list of options at the appropriate partition.

---

### Post by cdtech on 2009-01-12
Have you tried to create a folder on the root of the drive? In some cases only root has access to the root of the drive but users can create folders on the drive. How are you mounting the partition?

---

### Post by Greyed on 2009-01-12
> **SpinningAround said:**
> First is even a 400 GiB partition recommended with file system Ext3?

400Gb is perfectly fine.  The maximum partition size is defined in TiB.  Even at the smallest block size you're less than 25% of the way to the maximum size.

Further explanation here: [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

