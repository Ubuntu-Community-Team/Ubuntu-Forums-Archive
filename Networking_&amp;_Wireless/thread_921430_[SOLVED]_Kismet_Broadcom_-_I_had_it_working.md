---
title: "[SOLVED] Kismet Broadcom - I had it working"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by MarlonDean on 2008-09-16
Hi,

I had kismet working with my broadcom 4311. So feeling confident I gave my machine a well needed format and set out to install kismet again.

Guess what, I cant get it working again.

Here is what I did -

Downloaded the newest code from [www.kismetwireless.net](www.kismetwireless.net) (2008-05)

./configure
make dep
make
sudo make suidinstall


Edited the config file to 

source=bcm43xx,wlan0,broadcom

Ok, so when i run kismet, i get :

FATAL: Support for capture source type 'bcm43xx' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.

So I did this :


./configure --enable-bcm43xx 
make dep
make
sudo make suidinstall


Again I got the same error.

So i searched google and downloaded the 2007-10 version of kismet, but no help.

So can anyone tell me what to do? I know it is possible to run kismet using bcm4311.
Does anyone know how to completely remove kismet? maybe the different version screwed it up...



Please help!

---

### Post by MarlonDean on 2008-09-17
bump

---

### Post by rlzyoner on 2008-09-17
Temporary Fix:

Execute

[PHP]sudo kismet -C bcm43xx,wlan0,bcm[/PHP]

Assuming wlan0 is the interface you want kismet to use

---

### Post by MarlonDean on 2008-09-17
Thanks for the reply, I did as you said, but I still get :

FATAL: Support for capture source type 'bcm43xx' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.

How on earth do I compile kismet with bcm43xx support if --enable-bcm43xx does not work?

---

### Post by MarlonDean on 2008-09-17
OK, for those who suffer from the same problem- you need to install the libpcap devel headers before trying to compile kismet.

Now it works again!

---

