---
title: "Transfering Hard Drive?"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Peter1234123 on 2009-07-26
Is it possible, instead of ghosting the hard drive to simply physically move it to another machine? Will Ubuntu automatically load drivers for the new computer? (it's functioning as a server anyway, just needs to be able to run CUPS, Apache and FTP server). Thanks for your answer.

---

### Post by Whiffle on 2009-07-26
Yes!  I actually did this with a Debian install a little while ago.  Just be prepared with a live cd to rework your /etc/fstab and your /boot/grub/menu.lst if the order of your hard drives are different in the new computer.

---

