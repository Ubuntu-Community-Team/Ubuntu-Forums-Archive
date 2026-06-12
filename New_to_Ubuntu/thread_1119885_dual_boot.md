---
title: "dual boot"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by herbertg on 2009-04-08
Instead of the boot sequence being vista by default is there anyway to change it to ubuntu.

---

### Post by wolfen69 on 2009-04-08
```
sudo gedit /boot/grub/menu.lst
```
then, at the bottom of the text file, you will see all the entries for grub. simply move the vista section to where you want it.

---

### Post by Jakey_TheSnake on 2009-04-08
(i.e. below the first Ubuntu option)

If we have misunderstood, please rephrase.

---

### Post by cariboo on 2009-04-08
An even easier way to set the default boot instead of rearranging the menu is to change this line in /boot/grub/menu.lst:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default		0**
```

Count down the menu list starting at zero to the OS you want to boot by default. In my case when I was dual booting Windows was usually the 5th entry, so you would change default to 4.

Jim

---

