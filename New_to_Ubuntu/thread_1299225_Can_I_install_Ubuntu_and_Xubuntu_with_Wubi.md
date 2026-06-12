---
title: "Can I install Ubuntu and Xubuntu with Wubi?"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by wrgb2 on 2009-10-23
I have been running a Wubi install of Ubuntu for quite some time.  My question is, can I do a Wubi install of Xubuntu without overwriting the Ubuntu install?  If so, will Wubi automatically upate the boot loader so I can choose between Windows, Ubuntu and Xubuntu?  Also, if so, will I be able to see my Ubuntu filesystem from Xubuntu and vice-versa?

thanks,
Randy

---

### Post by Paqman on 2009-10-23
You don't need to reinstall to get Xubuntu. Just install the package xubuntu-desktop, log out, change you session to XFCE and log back in, and you'll be in Xubuntu's XFCE desktop instead of Gnome.

---

### Post by GimmeCoffe on 2009-10-23
Of course! On ubuntu terminal, just type ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```.

Then, on the logon screen, select "Choose Session" or something like that and choose XFCE, and wala! XUbuntu!

Hope it works!

~GimmeCoffe

---

### Post by wrgb2 on 2009-10-23
Thanks for the answers, guys.

Randy

---

