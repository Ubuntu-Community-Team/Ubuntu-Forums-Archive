---
title: "Broken SD Card format"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by akkad on 2009-05-17
i have an sd card that it seems (but am not sure) broken, some of the blocks on it are not readable, so far when i plug it, ubuntu detect it by placing an icon on the desktop, i can open it and browse some files and some files are corrupted, i can delete and paste on it.

anyway am looking to format it, first how can i know its path as a partition? am using this command to format "sudo mkdosfs -F 32 /dev/sdc0" but "no such file or directory" is the result??

if some blocks/sectors on the sd card are broken, is it possible to format it and fix the broken blocks?

---

### Post by mprince on 2009-05-17
In a terminal try typing:

```
sudo fdisk -l
```

Look for your media. Is it different than /dev/sdc0 ?

---

### Post by charliehorse55 on 2009-05-17
First off, use gparted. It will be a lot easier. 

Go to Applications > Add/Remove > Search for "gparted" and install the only result. 

When done installing, go to System > Administration > Partition Editor.

It should initially open with your main hard disk selected, got to the upper right corner and select your SD card. Then you be able to format it.

---

### Post by akkad on 2009-05-17
i know those stuff about fdisk and gparted, the problem is the sd card does not appear on both of them, but it is actually mounted on the desktop and i can access it files !!!!

---

