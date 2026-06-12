---
title: "loop devices"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by sazan on 2010-01-04
Hi

I was using losetup to use files as block devices. I created a file 'test' and fired the command -

losetup /dev/loop0 test

Under reboot, the mapping of the loop device was lost. Can I make loop devices persistent and how ? 

Also, is there any other way we can use regular files as block devices ?

---

### Post by blazemore on 2010-01-04
When you reboot, did the "device" disappear?
If not, you can just use /etc/fstab in the usual way, add a line like follows:
```
/path/to/device   /path/to/mountpoint   none   loop   0 0
```
That might work?

---

### Post by sazan on 2010-01-04
> **blazemore said:**
> When you reboot, did the "device" disappear?
If not, you can just use /etc/fstab in the usual way, add a line like follows:
```
/path/to/device   /path/to/mountpoint   none   loop   0 0
```
That might work?

Hi,

I entered followed entry into /etc/fstab 

/dev/loop0              /root/test          none    loop            0 0

This doesn't seem to work. The loop devices were detached on reboot. Am I doing something wrong here ?

---

### Post by sazan on 2010-01-04
bump!! anyone?

---

