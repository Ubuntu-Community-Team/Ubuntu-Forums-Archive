---
title: "Xp vanished from boot menu"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by nu2u904 on 2010-01-22
9.10 dual boot worked fine. Then Xp vanished from boot menu. Xp still in grub-boot.lst. How do I access Xp?

---

### Post by gabo.cr on 2010-01-22
You should post this thread under Installation and Upgrades.
You also should look for /boot/grub/menu.lst and make sure XP is not commented, meaning that it doesn't have a "#" before it.

:D

---

### Post by nu2u904 on 2010-01-22
> **gabo.cr said:**
> You should post this thread under Installation and Upgrades.
You also should look for /boot/grub/menu.lst and make sure XP is not commented, meaning that it doesn't have a "#" before it.

:D
Thankyou Gabor.cr. Here is part of the printout:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by Sef on 2010-01-22
> You should post this thread under Installation and Upgrades.

Incorrect advice.  You click the report button and inform the Ubuntu Staff that it need s to be moved.

Moved to ABT.

---

### Post by gabo.cr on 2010-01-23
Type this command in terminal and compare it to what you have on Grub:

```
sudo fdisk -l
```

---

