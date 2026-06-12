---
title: "Can't find /etc/fstab file"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by E.Maher on 2011-03-03
Hello,

I have a dual boot system, and recently I have installed xfce on my Ubuntu 10.10. There my NTFS partitions doesn't seem to be automatically mounted, contrary to gnome. After some reading I understood I have to change either the fstab or the mtab file. The Problem i I can't find them any where. unfortunately I couldn't find an answer else where..

many thanks for your help!

---

### Post by Verbeck on 2011-03-03
the file *should* exist!
open a terminal or alt+F2 and enter
```
gksu gedit /etc/fstab
```replacing gedit with mousepad or any other text editor you want

---

### Post by E.Maher on 2011-03-03
Never mind, I found it!! I guess I was blind ;)

Thanx a lot for your help though!

---

### Post by seawolf167 on 2011-03-03
Take a look at the fstab link in my sig for info on how to add an fstab entry. If you post the output of the following commands I can tell you what you need to add

```
sudo fdisk -l
blkid
mount
```

---

