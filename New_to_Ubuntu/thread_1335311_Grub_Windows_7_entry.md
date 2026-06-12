---
title: "Grub Windows 7 entry?"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by BOBSONATOR on 2009-11-23
So i have been at this for the past half-hour with no avail. Idk what gives.

here is my fdisk -l
```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        8359    67039232    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            8360        9729    10999800    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5            9667        9729      498928+  82  Linux swap / Solaris
/dev/sda6            8360        9667    10500808+  83  Linux

```

Here is my windows entry in menu.lst
```

# (1) Windows
title Windows
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```

and i get an error 15: file not found

Thanks

---

### Post by Lithium Rain on 2009-11-23
Take a look at [http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)

---

### Post by louieb on 2009-11-23
Everything looks alright. Lets take a deeper look.
Please follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by gackt on 2009-11-24
if you have try anything and still doesnt work try this:
rootnoverify (hd0,1)

---

