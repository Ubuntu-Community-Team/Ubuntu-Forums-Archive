---
title: "cant save sources.list"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Dr.iCe on 2009-07-20
so well i could do this earlier without ANY problems but now everything seems just F'ed up
it give me an warning and says i cant save :S
any suggestions..
what i am doing is trying to reinstall Wine but i cant because i have to remove a line from the that file. (need to reinstall wine because steam wont install or anything :S)

---

### Post by BinaryFeast on 2009-07-20
You probably need to open the file with root permissions before you edit it. Move to the directory and:

```
sudo gedit sources.list
```

---

### Post by drs305 on 2009-07-20
This command should work (use whatever graphic editor you wish):
```

gksudo kate /etc/apt/sources.list  #kubuntu
gksudo gedit /etc/apt/sources.list #ubuntu

```

Please use gksudo rather than sudo for graphical apps such as gedit/kate/nautilus, etc.

If it doesn't, give us the exact error message and try to run "sudo blkid" to see if any admin command is working for you.

---

### Post by wojox on 2009-07-20
Open a terminal:

```
gksudo gedit etc/apt/sources.list
```

---

### Post by Dr.iCe on 2009-07-20
> **BinaryFeast said:**
> You probably need to open the file with root permissions before you edit it. Move to the directory and:

```
sudo gedit sources.list
```
lol i forgot to open with root perm's ^^

thx man

---

