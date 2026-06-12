---
title: "Complete Noobie.... missing a nic"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by sikslk on 2006-08-16
Hi

first time poster so be nice :-({|= 

Had a xubuntu install done for me since it was causing major problems for myself not detecting hard drive problems. :(  Long story short:

It has teh onboard 100mb card installed and working (using now)

but the computer also has a dlink DGE530T gig card in it but i can see it in the networking area?

please help

---

### Post by sikslk on 2006-08-17
ok iv got the drivers for the card but trying to follow the instructions and getting an error straight up :frown: 

install linux driver as following command:

0. tar xvzf sk98lin.tgz, then goto sk98lin dir.
1. make all
2. insmod sk98lin.o
3. ifconfig eth0 up 10.xxx.xxx.xxx netmask 255.0.0.0

this is the first bit of the install and i have the files saved on the desktop and when i enter teh first line i get:

tar: sk98lin.tgz: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now 
tar: Child returned status 2 
tar: Error exit delayed from previous errors


Any help??? 
Please help:D

---

### Post by Return Privacy on 2008-06-02
Hi,
I installed a new D Link DGE-530T gigabit card and it is not seen in Ubuntu 7.10? The readme from D Link is worthless, just like what they told you above. Those commands DO NOT WORK! Can anybody please tell us how to install the driver for this D Link gigabit net card?
The file from Dlink download is named "dge530_driver_linux_610.tar"
I copied it to the desktop in ubuntu. I double clicked on it and it opens it to several other files. But, that does NOT install the driver to the card? 
Can someone please explain in english how to get the driver installed from this .tar file? Don't tell me to "compile a source" or whatever, because that means nothing to me. You guys need to explain step by step "how" to move this driver to "where" it belongs. Don't just assume that we all know what the hell "compile" and "source" and ".tar" means......I certainly don't. Not yet anyway. I can't believe how difficult it is to put in a network card and install the driver for it in Ubuntu. I was told that you didn't need to know any command lines to use Ubuntu? There has got to be an easier way to install drivers? Am I missing something? 
Any help will be greatly appreciated.

---

