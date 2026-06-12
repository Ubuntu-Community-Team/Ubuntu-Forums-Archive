---
title: "no such device ???"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by CellAlive on 2010-03-12
I have been trying out Ubuntu 9.10 for a few months when I a couple of days ago at startup got the message "no such device" and no boot menu. I found a thread on this forum (I can not find it anymore) where I was advised to erase the line "search--nofloppy--" from the bootmenu and got Ubuntu up and running. Following the advise I tried to execute: "sudo gedit/usr/lib/grub/grub-mkconfig_lib" but got only "command not found" or sometimes "[sudo] password for...." as a response. I have tried to reinstall Ubuntu, format the hard drive and reinstall Ubuntu etc. but nothing seems to help. Any hints?

---

### Post by plucky on 2010-03-12
> **CellAlive said:**
> I have been trying out Ubuntu 9.10 for a few months when I a couple of days ago at startup got the message "no such device" and no boot menu. I found a thread on this forum (I can not find it anymore) where I was advised to erase the line "search--nofloppy--" from the bootmenu and got Ubuntu up and running. Following the advise I tried to execute: "sudo gedit/usr/lib/grub/grub-mkconfig_lib" but got only "command not found" or sometimes "[sudo] password for...." as a response. I have tried to reinstall Ubuntu, format the hard drive and reinstall Ubuntu etc. but nothing seems to help. Any hints?

The command is ```
gksudo gedit /usr/lib/grub/grub-mkconfig_lib
```
Note the space between gedit and /usr.

I would make a copy of that file before you edit it just in case it

Good Luck

---

### Post by CellAlive on 2010-03-14
**Thank you plucky. **This comment made all the difference: "Note the space between gedit and /usr." I am up and running again.

---

