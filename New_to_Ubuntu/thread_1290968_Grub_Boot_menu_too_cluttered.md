---
title: "Grub Boot menu too cluttered"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by deancasino on 2009-10-14
hey guys, my Grub boot menu is too cluttered I have like 4 of everything (linux wise) is there a safe way I can modify the list?

---

### Post by linux phreak on 2009-10-14
You may be having the old kernels after the updating the system.Check this link for more info.
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by hellblazer on 2009-10-14
You can edit your menu.lst file.

It's in the /boot/grub/ directory of your system

I'd recommend using comments (# at the start of the line) to make sure you don't lose something important.

---

### Post by 73ckn797 on 2009-10-14
> **hellblazer said:**
> You can edit your menu.lst file.

It's in the /boot/grub/ directory of your system

I'd recommend using comments (# at the start of the line) to make sure you don't lose something important.

In a terminal enter:
```
gksudo gedit /boot/grub/menu.lst
```
Then follow the recommendation per hellblazer and comment out the earlier entries. If you no longer desire to have the old kernels installed you can remove those using System/Administration/Synaptic Package Manager. Once you have removed the earlier kernels you can delete those related entries from the "menu.lst". Keep in mind the file extension is not a 1 but a "l" (little L).

---

