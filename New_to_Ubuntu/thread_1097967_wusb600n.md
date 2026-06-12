---
title: "wusb600n"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by monoiz15 on 2009-03-16
hey i got a linksys usb daul band wireless n adapter from the store.. it said its made for windows but my friend let me borrow a wireless g one of his that worked. im sure theres a way to get it working in linux. does anyone think they can help me out?? the model is the wusb600n.

---

### Post by halitech on 2009-03-16
open a terminal and with the usb adapter not plugged in, post the output of
```
lsusb
```then plug the adapter in, wait a minute and run the same command and post the output

---

### Post by Kevbert on 2009-03-16
If you have the Windows **XP** driver files (.sys .inf) then it's possible to install these with ndiswrapper and ndisgtk. ndisgtk is the application that will show up under System-Administration-Windows Wireless Drivers. Both files can be found on the Ubuntu installation CD under /pool/main/n. Just double click on the .deb file to install the applications.

---

### Post by monoiz15 on 2009-03-16
thank you so much! i had some drivers that i didnt really get how to work but i put it in ndisgtk and now it works!! thanks

---

### Post by Castor68 on 2009-03-21
I had the same problem with my WUSB600N. I installed both ndisgtk and ndiswrapper. Through System-Administration-Windows Wireless Drivers I installed a driver from the wireless adapter CD and... it works perfectly now !!!

---

### Post by monoiz15 on 2009-03-22
yea mines good now too. i had the drivers i just didnt no to use the windows wireless drivers.. i had seen them before but forgot..

---

### Post by t_virus on 2009-03-25
is there any other way to get it working without ndiswrapper or ndisgtk?
i have an atheros 5007 eg and its working with madwifi-hal and i'm afraid that if i install ndiswrapper i cant use aircrack-ng with may atheros.
any help about this?

---

### Post by Castor68 on 2009-04-11
[COLOR="Red"]aircrack-ng[/COLOR] ..... mmmmmmmmmmmmm

---

### Post by Gemu on 2009-06-17
I have the same card and had it working with the modifyed driver found in another tutorial I found on here but not now. Do you have to undo all that before you can go the ndsiwrapper route?

---

### Post by A4orce84 on 2010-01-17
update:

Does it still work in Ubuntu 9.10 with windows wireless drivers?

I'm having issues. =(

Thanks.

---

