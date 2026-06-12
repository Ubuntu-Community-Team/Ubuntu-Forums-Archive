---
title: "dell inspiron 1520"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by amarino15 on 2010-09-01
hey guys, i'm trying to install ubuntu 10.04.1 on my dell inspiron 1520

graphics card is a nvidia 8600M GT
2gb of ram

i'm using the alternate text based installer on a dvd.

the system was running windows 7 until i formatted the hd and installed ubuntu while the hd was blank. the installation goes well until the its finalized and the system reboots.

when i reach what i assume is the ubuntu startup screen all i am able to see are some vertical lines which appear to be in the basic ubuntu color scheme. ill attach a picture of the screen i see.

i dont know what is going on here, Ctrl+Alt+F2 brings me to another distorted screen. i'd try to boot to safe mode using grub but the system goes straight to ubuntu and bypasses grub.

im thinking it may be a screen resolution issue, is there any way to change the screen reso without actually being able to see the screen?

can anyone help?

---

### Post by BrandyBear on 2010-09-01
Well technically no but if you have the windows recovery disk go back to windows then read the ubuntu release notes that should help

---

### Post by amarino15 on 2010-09-01
so reinstall windows? heh

---

### Post by BrandyBear on 2010-09-01
Yes if you re install windows then read ubuntu's relese notes and Known Bugs.....Or have you partitoned it?

---

### Post by amarino15 on 2010-09-01
no windows was wiped, but i can get into grub by holding shift lol

edit: is there a command to change the default resolution on ubuntu using grub? 

shot in the dark but i think it may work

---

### Post by amarino15 on 2010-09-01
problem solved:

i was refered to this:

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

had to check nomodeset during the install

---

