---
title: "Help needed with ipw2200"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by colinireland on 2007-08-18
Hey,

I have a question about packet injection using the ipw2200 driver. I am using a Dell Inspiron 6000 & Feisty. I dont mean to plague people with yet another question on thi topic but I am in dire straits!

 I patched my drivers like so:

I installed the ieee80211-1.2.17 library,
then patched the drivers
         %patch ipw2200-1.2.1/ipw.c ipw2200-1.2.1-inject.patch
         %patch ipw2200-1.2.1/Makefile ipw2200-1.2.1-inject_Makefile.patch
         %cd ipw2200-1.2.1
         %sudo ./remove-old
         %sudo make
         %sudo make install

         %sudo rmmod ipw2200
         %sudo modprobe ipw2200 rtap_iface=1

I then edited the file /etc/modprobe.d/options to contain options ipw2200 rtap_iface=1

When I tried the injection test I recieved no answer and all attack modes failed. Does anyone know where I have gone wrong? Do you need more information? Any help would be greatly appreciated as I have been fooling around with this for some time now with no positive results.

regards,
Colin

---

