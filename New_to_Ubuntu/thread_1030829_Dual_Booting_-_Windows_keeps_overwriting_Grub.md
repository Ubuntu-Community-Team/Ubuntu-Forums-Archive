---
title: "Dual Booting - Windows keeps overwriting Grub"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by registernow on 2009-01-04
Hey i dual boot with windows xp/ubuntu 8.10

problem is everytime i boot into windows, it seems to overwrite grub (i'm really not sure whats going on there)..

so to boot back into ubuntu i have to do these steps everytime (tedious..)


boot live cd
run these commands:

sudo grub
find /boot/grub/stage1 (which replys with (hd0,1)
root (hd0,1)
makeactive


but how do i make it so so that windows stops overwriting grub all the time?

---

### Post by registernow on 2009-01-04
halp

---

### Post by adult swim on 2009-01-04
whenever you do your steps you mentioned above, instead of putting in makeactive, try using ```
setup (hd0)
``` instead

---

### Post by registernow on 2009-01-04
thanks, ill give it a shot now

---

