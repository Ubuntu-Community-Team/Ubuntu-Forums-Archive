---
title: "rarcrack output segmentation fault"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by twaher on 2010-10-09
hi..I encounter a problem while using rarcrack..each time am trying to remove the password of a zip  file, rarcrack displays " Segmentation fault" .the file is on my desktop.

while accessing it in terminal, here is the display:

twaher@ubuntu:~$ cd Desktop
twaher@ubuntu:~/Desktop$ rarcrack carla.zip
RarCrack! 0.2 by David Zoltan Kedves (kedazo@gmail.com)

Segmentation fault
twaher@ubuntu:~/Desktop$

i have also done sudo apt-get remove --purge unrar && sudo apt-get install unrar-free ....but this does not solve the issue..can anyone help please? thanks

---

### Post by techdude3177 on 2010-10-09
Try the following:

```
rarcrack carla.zip --threads 2 --type zip
```

---

### Post by twaher on 2010-10-10
thanks really appreciate..it seems to be working but taking lots of time to crack it due to numerous possibilities..

---

