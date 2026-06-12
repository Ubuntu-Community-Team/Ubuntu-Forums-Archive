---
title: "error on install"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Simplemind169 on 2009-02-20
i just installed kubuntu to my laptop and rebooted it seemed fine untill it loaded.
i get this error: ALERT! /dev/disk/by-uuid/d468948c-25e0-4eb8-9b2c-686e125da415 does not exist
please help

---

### Post by tarps87 on 2009-03-12
Can you boot using the live cd and past the contents of the /etc/fstab from the hard drive, can you also post the output of
```
sudo fdisk -l
```
and
```
sudo blkid
```
You will need to enter these in the terminal
Applications -> accessories -> terminal

---

