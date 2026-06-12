---
title: "Ubuntu boot issue with Super Grub"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Heliman5 on 2008-12-29
I am Currently dual booting XP and Ubuntu. When I try to boot Ubuntu It Tries to boot from (hd2,2), but Ubuntu is on (hd0,2). I have to change it in Super Grub every time. is there a way to make the change permanent?

---

### Post by caljohnsmith on 2008-12-29
How about opening a terminal (Applications > Accessories > Terminal) while you are in Ubuntu and do:
```
gksudo gedit /boot/grub/menu.lst
```
And then you can change all the Ubuntu entries to use (hd0,2). Also, change the line that says "# groot=(hdX,Y)" to be:
```
# groot=(hd0,2)
```
And then you should be all set. Let me know how it goes or if you run into problems.

---

### Post by Heliman5 on 2008-12-29
Works great! It took all of thirty seconds;)

---

