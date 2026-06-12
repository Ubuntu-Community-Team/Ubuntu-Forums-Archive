---
title: "Dual Boot ubuntu/vista"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by keygiwawah on 2009-03-09
How do you set the preferences as to which operating system is default to boot on start-up?

---

### Post by kanikilu on 2009-03-09
You can either manually edit the /boot/grub/menu.lst file or install and use the "startupmanager" package (in the repos).

---

### Post by keygiwawah on 2009-03-09
ok, thanks

---

### Post by x33a on 2009-03-09
```
gksudo gedit /boot/grub/menu.lst
```

find the line with
> default 0

change it to the number windows is listed at. start counting from 0.

e.g., if it's at 3rd number, then
> default 2

---

