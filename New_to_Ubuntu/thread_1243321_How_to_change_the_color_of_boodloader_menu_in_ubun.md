---
title: "How to change the color of boodloader menu in ubuntu 9.04?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by karthick87 on 2009-08-18
I am using windows XP and Ubuntu 9.04,My bootloader menu appears to be  black in color,How to change this color??I know it is possible by installing StartUP-Manager,But can someone tell a manual way to do this??

---

### Post by philinux on 2009-08-18
It's much easier with the gui. If you mess up editing menu.lst ubuntu might not boot.

To see it's contents look here.

```
cat /boot/grub/menu.lst
```

[http://www.gnu.org/software/grub/manual/grub.html#color](http://www.gnu.org/software/grub/manual/grub.html#color)

---

### Post by karthick87 on 2009-08-18
Yeah thankyou,it helped,Cheers!

---

