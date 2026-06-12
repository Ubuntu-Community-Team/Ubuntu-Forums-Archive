---
title: "MBR lists is growing after reinstalling ubuntu"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by JPORTIL on 2009-07-06
Hello,

I some how managed to mess up installing ubuntu remix the first time, so I tried it again and now I have more than one instance of ubuntu in my mbr.  How can I remove the extra instance?  I have my netbook setup as a dual boot system.  Currently when I boot my computer is showing Linux, Linux, and Windows XP, the first linux selection being faulty.

---

### Post by cariboo on 2009-07-06
You can edit /boot/grub/menu.lst and remove the extra Linus selection that doesn't work. To edit the file press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

Then remove the first occurrence of Linux in the menu.

---

### Post by JPORTIL on 2009-07-07
Thank you.

---

