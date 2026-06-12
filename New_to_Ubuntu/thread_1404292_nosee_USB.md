---
title: "nosee USB"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by bjje on 2010-02-11
I installed 9.1 into an old Dell and put in a USB card that it Linux-friendly but removable drives don't show up when I plug them in. 
Likewise USB wifi gear.
I don't see system preferences>removable drives in the menu, Where do I tell Ubuntu to look for them?
thankyoos

---

### Post by mwcrowley on 2010-02-11
after you plug in the usb card, enter dmesg at the command line.  At the end of the output you'll see some lines regarding the usb card.  If it's a storage device it should pop up in nautilus.  If it's a wifi cared you'll see output from the dmesg command.  Some wifi cards require some trouble shooting.  Or your usb port could be shot.

---

