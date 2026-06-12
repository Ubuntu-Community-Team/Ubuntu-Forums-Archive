---
title: "Accessing Hard Disk"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by ikon_ on 2009-08-20
Well,  I have Ubuntu 8.10 . well I also have windows on my hard disk and two other partitions .When I connect my 1TB of Hard Disk  to my laptop and boot my Ubuntu I am not able to access other partitions of my hard disk . Is this because Ubuntu cannot support such large amoutn of memory or is there anything wrong with my  settings .  Can somebody help :confused:

---

### Post by blazemore on 2009-08-20
With the hard drive plugged in
Go to Applications -> Accessories -> Terminal

Type
```
sudo fdisk -l
```

Please post the results here, preferably within [ code] tags

---

### Post by LewRockwell on 2009-08-20
> **ikon_ said:**
> Well,  I have Ubuntu 8.10 . well I also have windows on my hard disk and two other partitions .When I connect my 1TB of Hard Disk  to my laptop and boot my Ubuntu I am not able to access other partitions of my hard disk . Is this because Ubuntu cannot support such large amoutn of memory or is there anything wrong with my  settings .  Can somebody help :confused:

we'll need more specific information to make any informed suggestions

however, if we were to assume that you are booting an installation of Ubuntu that is located on your 1TB external hard drive then it is possible that your internal hard drive is not being mounted

food for thought

.

---

### Post by blazemore on 2009-08-23
Please post the results of
```
sudo fdisk -l
```
That will help immensely!

---

