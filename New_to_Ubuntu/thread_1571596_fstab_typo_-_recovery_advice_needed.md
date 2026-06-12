---
title: "fstab typo - recovery advice needed"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by GaryTheCat on 2010-09-09
hello -I'm stupid.

I edited my fstab with the line sdb when I meant sda

and now the machine hangs (but it does offer a command prompt

how can I undo my mess?

Many thanks

G

---

### Post by MrWES on 2010-09-09
hit the ESC hit at right before boot up. choose recovery mode, and then edit the /etc/fstab file, reboot.

---

### Post by baddnady23 on 2010-09-09
Or you could boot up in the live CD, mount your ubuntu filesystem drive, and edit fstab to what you need.

---

### Post by garner_nc on 2010-09-09
Before I go editing system files I make a copy:

cp fstab fstab.bak

then if (when) I screw something up, recovery is simply copying the backup file to the old filename.

All the Best,
D. White

---

