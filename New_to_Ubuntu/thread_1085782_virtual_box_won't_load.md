---
title: "virtual box won't load"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Midgetprawn on 2009-03-03
I am new to the virtual world and a fledgling in Ubuntu but I had Vbox working and now it says


Could not load the settings file '/home/kevin/.VirtualBox/VirtualBox.xml'.
Cannot convert settings from version '1.6-linux'.
The source version is not supported.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
VirtualBox
Interface: 
IVirtualBox {557a07bc-e6ae-4520-a361-4a8493199137}


I am running 8.10 with the kernels up to date, in fact I tried earlier versions to cross check.

Any suggestions?

---

### Post by Fire_Chief on 2009-03-03
It looks like you're trying to use an old version of Vbox? Try downloading the latest one from Sun at [http://dlc.sun.com/virtualbox/vboxdownload.html#linux]("http://dlc.sun.com/virtualbox/vboxdownload.html#linux"). Install the new version and try running it again.

-Cheers!

---

### Post by Midgetprawn on 2009-03-03
Tried that :(
It won't install because I keep getting a conflict message even though I have uninstalled virtualbox-ose in synaptic. Are there residual files which could cause conflict?

---

### Post by Fire_Chief on 2009-03-03
Not sure, what does the conflict message say?

---

