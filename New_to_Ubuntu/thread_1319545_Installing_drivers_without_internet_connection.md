---
title: "Installing drivers without internet connection"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by yellowstoned on 2009-11-08
Just got Linux running on a tx1000 laptop and I am trying to get the drivers up and going

I connect using a Pantech USB wirless broadband connection with Altel, so I have no way to get a wi-fi or ethernet connection at the moment on this laptop but I want to install drivers for the touch screen audio ect. I have downloaded a selection of drivers on my desktop and have them on a portable hard drive. Do i need to place them in a particular folder to get Linux to recognize them as programs it can install?

Any tips for the Nvidia drivers, they are proving to be a major pain, I have tried other fourms on here but the old steps are not working for me. 

thanks!

---

### Post by danill2008 on 2009-11-08
> **yellowstoned said:**
> Just got Linux running on a tx1000 laptop and I am trying to get the drivers up and going

I connect using a Pantech USB wirless broadband connection with Altel, so I have no way to get a wi-fi or ethernet connection at the moment on this laptop but I want to install drivers for the touch screen audio ect. I have downloaded a selection of drivers on my desktop and have them on a portable hard drive. Do i need to place them in a particular folder to get Linux to recognize them as programs it can install?

Any tips for the Nvidia drivers, they are proving to be a major pain, I have tried other fourms on here but the old steps are not working for me. 

thanks!

Firstly you cannot install .exe files on linux, but you can install wine and that whats you can use to install windows software, but in this case it would'nt work, because you want to install drivers and for that you cannot emulate it. I suggest searching the Hardware drivers, this can be found at System > Administration > Hardware Drivers. Run that and install the drivers it lists. Also why doesn't your usb broadband connection work?

---

### Post by Shazaam on 2009-11-08
Have you been here yet?...
[https://help.ubuntu.com/9.10/add-applications/C/index.html](https://help.ubuntu.com/9.10/add-applications/C/index.html)

Main page...
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by yellowstoned on 2009-11-08
I am probably messing up the terminology a bit, the files I have downloaded on my desktop are for linux. 

I cant seem to get the usb broadband card to recognize itself it is a Pantech card and I can not find anywhere to activate it or command it to dial my connection within linux, perhaps I will try emulating it with wine.

---

### Post by Primefalcon on 2009-11-08
> **yellowstoned said:**
> I am probably messing up the terminology a bit, the files I have downloaded on my desktop are for linux. 

I cant seem to get the usb broadband card to recognize itself it is a Pantech card and I can not find anywhere to activate it or command it to dial my connection within linux, perhaps I will try emulating it with wine.
well if they're .deb or .sh which means are executable filetype, just double click to run them

---

