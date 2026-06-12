---
title: "How to remove ubuntu"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by schuthof on 2009-02-22
I like ubuntu just as much as windows vista home premium (sorry!), but every time I have to restart my system (athlon 64 x2 4200) it first shows ubuntu. I want to be free, and only see ubuntu at my own volition. However...I cannot remove it via the usual windows system. How to remove ubuntu? (I still have it on CD) thanks for your help!

---

### Post by kansasnoob on 2009-02-22
> **schuthof said:**
> I like ubuntu just as much as windows vista home premium (sorry!), but every time I have to restart my system (athlon 64 x2 4200) it first shows ubuntu. I want to be free, and only see ubuntu at my own volition. However...I cannot remove it via the usual windows system. How to remove ubuntu? (I still have it on CD) thanks for your help!

Is this a dual boot or a Wubi install? I don't quite understand the situation.

Does it boot into Ubuntu before you can access Windows? That would tell me you used VM Ware or Virtual Box.

If it's a dual boot you should have the choice of booting either (or any) OS and the default can be changed easily by installing startupmanager in Ubuntu.

---

### Post by sarath_it on 2009-02-22
> It first shows ubuntu

in the menu? You can change the boot default in grub.

sudo gedit /boot/grub/grub.conf to change default

Look for a line
default 0

change the number to the windows partion position in the list (list counts from 0)


better yet, make it saved - it will restart in the last operating system..
default saved

---

