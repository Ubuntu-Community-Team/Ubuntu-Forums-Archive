---
title: "grub list"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by rhuea on 2009-12-28
hi, i recently updated my ubuntu 9.10 and found a new set of choices in my grub menu. i tried the usual gksu gedit /boot/grub/menu.lst command but my laptop only gave a blank document. how do i edit the grub in this release? many thanks.

---

### Post by drs305 on 2009-12-28
If you are using Grub 2 (you can see the version in the Grub menu. Currently "Grub 2" is version 1.97beta for Ubuntu), the file structure has completely changed.

There are various links in my signature line. "GRUB2" is the community doc link.

"G2-Basics" is the thread in these forums on which the community doc was based. It also contains links to many other excellent posts on Grub 2 on this and other forums.

---

### Post by audiomick on 2009-12-28
Hi.
You have likely acquired grub2 instead of grub. Was it a fresh install?

Anyway, look here.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by ranch hand on 2009-12-28
To be sure what version of grub you are running do;
```

grub-install -v

```
in terminal.

drs305s instructions are very good.  Use them.

There is a simplified grub2 intro in my sig.  The first 2 links in it are the best there is (the 2nd in Grub2 Basics).

---

