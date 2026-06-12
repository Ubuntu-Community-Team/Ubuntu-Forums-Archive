---
title: "Vga=771 is depreated"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by Zack579 on 2010-12-13
hi,
i am new to ubuntu...when i boot to ubuntu i get this error

"Vga=771 is depreated,use set gfxplayload=800x600x8,800x600 before linux command instead"

sometimes i can log in to ubuntu and sometimes not

i have ubuntu 10.10 installed inside windows xp sp3 using wubi

please help..

---

### Post by Zack579 on 2010-12-13
hi,
i am new to ubuntu...when i boot to ubuntu i get this error

"Vga=771 is depreated,use set gfxpayload=800x600x8,800x600 before linux command instead"

sometimes i can log in to ubuntu and sometimes not

i have ubuntu 10.10 installed inside windows xp sp3 using wubi

please help..

---

### Post by oldfred on 2010-12-13
Did you upgrade from a old version. It copied the vga parameter into your grub2.

More info here.
vga=799 is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)

Look in this file for the vga=xxx & adding the gfxpayload line
gksudo gedit /etc/default/grub

---

### Post by oldfred on 2010-12-13
Please do not create duplicate threads.


Posted response in this one:
[http://ubuntuforums.org/showthread.php?t=1644531](http://ubuntuforums.org/showthread.php?t=1644531)

---

### Post by Zack579 on 2010-12-14
i am sorry....

---

### Post by Zack579 on 2010-12-14
thanks for the reply...i got it fixed by reinstalling the Ubuntu...

thank you

---

### Post by overdrank on 2010-12-14
Hi and welcome, threads merged. :)

---

