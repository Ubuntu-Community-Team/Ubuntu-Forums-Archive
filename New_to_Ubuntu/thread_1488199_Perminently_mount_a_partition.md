---
title: "Perminently mount a partition?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by jakeeee on 2010-05-19
When I start my ubuntu partition I was my storage partition to mount automaticly.
Is that possible?

---

### Post by SlidingHorn on 2010-05-19
If you're looking to mount your storage partition from ubuntu, open a terminal, and run:

```
sudo fdisk -l
```

Find your partition and enter the following:

```
sudo mount -t ntfs -o nls=utf8,umask=0222 <your/storage/partition*> /media/c
```

You don't have to name it /media/c - it's just what I use when I mounted my Windows partition

If you choose to unmount, do:

```
sudo umount /media/c
```

This will allow you to access your partition on ubuntu...

---

### Post by jakeeee on 2010-05-19
I know how to acsess it.
I want it to mount on startup..
Those commands will do that for me?

---

### Post by linuxman94 on 2010-05-19
You can use an easy GUI program called pysdm.  CLick [here]("apt:pysdm") to install it and then you can find it in System -> Administration -> Storage Device Manager.  You can then use it to set up an automount for your partition.

---

### Post by jakeeee on 2010-05-19
That'll work :D Thanksss!

---

### Post by sandyd on 2010-05-19
alternatively, you can also use [ntfs-config]("apt:/ntfs-config") for NTFS partitions.

---

### Post by pizza-is-good on 2010-05-19
> **carlee said:**
> alternatively, you can also use [ntfs-config]("apt:/ntfs-config") for NTFS partitions.

I use that for mine. Works without problems.

---

