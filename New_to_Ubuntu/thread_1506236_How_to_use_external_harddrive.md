---
title: "How to use external harddrive"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by dtommy79 on 2010-06-10
Hi,

I have an extarnal harddrive but when I plug it in, nothing happens.

Do I have to do something else to get it work?

---

### Post by zeroseven0183 on 2010-06-10
Would you know if what file system your hard drive is using?

You can either check it with
a. Gparted (if you have it installed), or
b. Disk Utility

How about when you plug it to other computers, is it recognized?

---

### Post by dtommy79 on 2010-06-10
The problem is the system cannot see it so I can't check it.

I used it on my windows computer, but I need some files backed up from my linux computer.

---

### Post by PhilDawg09 on 2010-06-10
> **dtommy79 said:**
> The problem is the system cannot see it so I can't check it.

I used it on my windows computer, but I need some files becked up from my linux computer.

You might have to reformat the drive in a Linux/ubuntu/kubuntu etc, format which I do  not know right off top my head, as I am new to this Ubuntu OS.

---

### Post by marbertone on 2010-06-10
see if a new folder is created in /media/, e.g.

```
 ls /media/ -lrt 
```

Cheers!
Mario Alberto

---

