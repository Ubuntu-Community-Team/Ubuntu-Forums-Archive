---
title: "USB NOT appear on desktop after plugging in"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by skyeric on 2010-04-19
Hey, how can I make my USB memory stick not appear on the desktop after i plug it in..? any ideas?

Thanks in advance,
Eric

---

### Post by 2hot6ft2 on 2010-04-19
Open a terminal
Applications > Accessories > Terminal
and run
```
gconf-editor
```
in the left go to
Apps > Nautilus > Desktop
On the right Uncheck the bottom option which is
volumes_visible

All done close it then the terminal

---

### Post by Calash on 2010-04-19
You can also run into this behaviour if you have Virtualbox and your user is part of the vboxuser group.  I can usually get around it by removing myself from the group and then adding it back.

If you do not use Virtualbox you can just ignore this ;)

---

### Post by skyeric on 2010-04-19
thanks worked perfectly :)
not using virtualbox but thanks anyway.

thanks for the help,
Eric

---

