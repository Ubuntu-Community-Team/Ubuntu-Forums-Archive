---
title: "finding /dev/sdc drive"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by adza on 2009-03-28
hello, this is a stupid question.. but... how do i find out where /dev/sdc is on the hardware map? ie, is it hd(0) or hd(1,0) etc etc.. during the last install it seems that grub has forgotten where my windows partition is... it has the entry in grub as hd(0,0)... 

p.s. the great bit about this story is that this was installed about two months ago... just got around to checking the windows install today!! haha

---

### Post by Elfy on 2009-03-28
For the drives

sda is hd0
sdb is hd1
sdc is hd2

Partitions number from zero in the same way

sda1 is hd0,1
sda2 is hd0,1
sdb1 is hd1,0
sdb2 is hd1,1

etc

```
cat /boot/grub/device.map
```

---

