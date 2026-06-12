---
title: "help with floppy drive"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Bert1e on 2008-12-14
New to linux but I want to get it up and running on p3

I am having a problem with floppy drive not being loaded by ubuntu 8:10 It works ok with xp and mandriva linux and looking at your forums it seems it is a problem with ubuntu. I need a step by step guide on where to write the various solutions suggested on your forum please.

---

### Post by Michael.Godawski on 2008-12-14
Open the terminal
applications > accessories > terminal
run
```
sudo modprobe floppy
```
enter password and hit enter.

---

### Post by Bert1e on 2008-12-15
I now have the floppy drive and have tried an open office  document saved on a floppy disk. The file opens and I can edit it but when I try to save changes i get "general input/output error" notice. is there a fix please?

---

### Post by linux_tech on 2008-12-15
Try 

```
mount /dev/fd0
```

---

