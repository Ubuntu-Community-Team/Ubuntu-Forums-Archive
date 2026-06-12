---
title: "Password on boot sequence?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-02-12
I would like to eliminate the password on the BOOT sequence.  I think it probably is done in the Terminal, but my thinking has failed me in the past, often actually.

---

### Post by Dr Small on 2009-02-12
Are you prompted for a password before the POST screen, or after the GRUB boot menu?

---

### Post by kanikilu on 2009-02-12
If the password is asked for at the GRUB boot menu, I think you just need to comment out (or remove) the "password" line in the /boot/grub/menu.lst file.

---

### Post by Yed Ied on 2009-02-12
The boot is complete.  The final screen is locked untill give my password.

---

### Post by bodhi.zazen on 2009-02-12
That is the log in screen, GDM.

It is not advised to auto log in, but if you must google is your friend :

[http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html](http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html)

I trust you understand (and accept) the obvious security risks involved with your behavior.

---

