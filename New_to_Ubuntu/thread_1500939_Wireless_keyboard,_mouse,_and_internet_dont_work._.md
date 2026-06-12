---
title: "Wireless keyboard, mouse, and internet dont work. Day old user."
date: 2010-06-03
forum: New to Ubuntu
---

### Post by northeastbread on 2010-06-03
I just installed linux for the first time ever because i was interested in learning it. I run dual boot with windows 7 on a toshiba satellite a505. I have a microsoft arc keyboard and a wireless logitech mouse. both powered by usb hook ups. also, my wireless internet does not work. ive looked over some threads already and none have really been helpful. i have a realtek card i ran this code through terminal and it out put these two numbers for output:

Controller: 8172 (rev 10)
Subsystem: 8181

i know thats probably not what you guys need to help me, but any help would be much appreciated.

---

### Post by mapes12 on 2010-06-05
Applications>Accessories>Terminal ```
sudo lshw
``` then ```
sudo fdisk -l
``` and post the output back here. Wrap QUOTES around it. It's in the forum post tool bar.

---

