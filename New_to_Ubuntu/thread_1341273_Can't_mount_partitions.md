---
title: "Can't mount partitions"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by PHINCY L PIOUS on 2009-11-29
I HAVE INSTALLED UBUNTU ULTIMATE 2(8.10) IN MY DESKTOP.BUT SOME TIMES IT SHOWS ERROR MESSAGES ,SOME WHAT LIKE THIS
 
"Cannot mount the volume "
when i try to open my hard drive partitions.(The problem arises for other drives too ,except my root partitions,even when partitions are mounted during installation of ubuntu.)
can any one give me a solution for this problem?

---

### Post by mlentink on 2009-11-29
Linux, and thus Ubuntu doesn't know anything about drive letters, so it doesn't know about any 'D'-drives.

You could help us by opening up a terminal ( Applications>Accessories>Terminal)
and then type in the following (you can cut and paste if you like):
```
sudo fdisk -l
```Take care: that's a lower case L at the end, not the figure 1!
Ubuntu will come back to you with a bit of information. Please cut and paste that information here, and enclose it in 'code'-tags (select the text and then use the '#'-sign)

---

