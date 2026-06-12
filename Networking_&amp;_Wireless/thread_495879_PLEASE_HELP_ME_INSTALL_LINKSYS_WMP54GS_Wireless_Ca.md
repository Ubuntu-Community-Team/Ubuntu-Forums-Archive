---
title: "***PLEASE HELP ME INSTALL LINKSYS WMP54GS Wireless Card**"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by brick2thabone on 2007-07-08
I have started trying to install ndiswrapper in ubuntu in order to get my drivers to work. I am a bit new to the procedures for installing in linux. I need instructions on how to install ndiswrapper and the driver for my card. some expert help is greatly appreciated, I NEED INTERNET!! my wireless card is linksys wmp54gs. Thanks!

---

### Post by chicoicho on 2007-07-08
Install Automatix 2

---

### Post by kevdog on 2007-07-08
Lets just first determine the chipset of the card and then proceed accordingly.  (Dont just jump to automatix!)

Please type the commands at the command prompt and then cut and paste the output:
lspci -nn
lshw -C network.

---

