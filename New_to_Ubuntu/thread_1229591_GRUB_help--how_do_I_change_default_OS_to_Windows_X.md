---
title: "GRUB help--how do I change default OS to Windows XP"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by mnrobertson on 2009-08-02
I just installed Ubuntu 9.04 on my laptop.  It dual boots with Ubuntu as the default.  My wife also uses this laptop and wants to use Windows XP--how do I change GRUB so Windows is the first and default option?  We are both novices

---

### Post by ubudog on 2009-08-02
Check this out:[https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4](https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4)  Hope it helps!:)

---

### Post by gorgon on 2009-08-02
hi there,

you have to open a file called menu.lst and edit it:

```
gksudo gedit /boot/grub/menu.lst
```

in this file there's a line that says 'default' with a number after it (typically 0). The number represents which of the boot commands (towards the end of the file) that grub will execute as default.

mine looks like this:
```
title Windblows
rootnoverify (hd0,0)
makeactive
chainloader +1

title UbuntuStudio, kernel 2.6.27-7-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda7 ro splash vga=791
initrd /boot/initrd.img-2.6.27-7-generic

```

so if I want to boot winblows as default I set the number to 0, and if I want ubuntu as default I set the number to 1. And save.

Hope that helps

---

### Post by SunnyRabbiera on 2009-08-02
There is also a graphical tool for this too, its called startupmanager:
[http://packages.ubuntu.com/search?keywords=startupmanager&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=startupmanager&searchon=names&suite=all&section=all)

Just install the package for your version of ubuntu

---

