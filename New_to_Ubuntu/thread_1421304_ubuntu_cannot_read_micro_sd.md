---
title: "ubuntu cannot read micro sd"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by blizta on 2010-03-04
is there any driver  that make ubuntu recognize micro SD???

---

### Post by Peter09 on 2010-03-04
I understood that Ubuntu should see SD out of the Box, no drivers needed. What version are you running?

---

### Post by mikechant on 2010-03-04
How are connecting the microSD card? Via an SD slot and micro adapter, or via a USB adaptor?

microSD cards in general should work fine without extra drivers, however if Ubuntu doesn't understand the contents of the card(partitions/filesystems) it will be recognized as a device but the contents will not be mounted/ visible. Do you know what is supposed to be on the card?

After connecting the card, can you open a terminal (ALT+F2) and type the following commands and post their output:
```
lsusb
sudo fdisk -l
```

(Note the -l is a lower case 'L' not a number 1 - they look almost identical; also note you will need to type you password for the second command)

---

### Post by blizta on 2010-03-09
thanks......

finaly my ubuntu 9.10 can mount it :)

---

