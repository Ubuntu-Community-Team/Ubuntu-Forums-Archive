---
title: "Intel AC97 modem driver"
date: 2005-06-03
forum: Networking &amp; Wireless
---

### Post by sadiini on 2005-06-03
Well! Trying to install driver for my modem. Everything is ok. Driver compiled fine, but if I try to put it, where it belongs I get:

#root@arvuti:/home/###/proge/intel-2.60.80.1/intel-2.60.80.1 # insmod -f  Intel537.ko
insmod: error inserting 'Intel537.ko': -1 Operation not permitted
root@arvuti:/home/###/proge/intel-2.60.80.1/intel-2.60.80.1 #

Can anyone explain that in plain english? I am puzzled. 
Everything I did, was by the book (driver docs). 

 \\:D/  of Joy...

---

### Post by az on 2005-06-03
sudo insmod intel537.ko


You need to use sudo.  And try first without the -f

also, perhaps this will help?  Some intel mdems work with the sl-modem-drivers

[http://test.wiki.ubuntu.com/forum/hardware](http://test.wiki.ubuntu.com/forum/hardware)

---

### Post by sadiini on 2005-06-04
[QUOTE=azz]sudo insmod intel537.ko


You need to use sudo.  And try first without the -f

also, perhaps this will help?  Some intel mdems work with the sl-modem-drivers

[http://test.wiki.ubuntu.com/forum/hardware](http://test.wiki.ubuntu.com/forum/hardware)[/QUOTE]

Well! I do know, that it is Intel 537 (AC97) modem. Then again I have driver compiled and looks healthy  :) Still...
indrek@arvuti:~$ cd proge
indrek@arvuti:~/proge$ cd intel-2.60.80.1
indrek@arvuti:~/proge/intel-2.60.80.1$ cd intel-2.60.80.1
indrek@arvuti:~/proge/intel-2.60.80.1/intel-2.60.80.1$ sudo insmod Intel537.ko
Password:
insmod: error inserting 'Intel537.ko': -1 Operation not permitted
indrek@arvuti:~/proge/intel-2.60.80.1/intel-2.60.80.1$ sudo insmod -f Intel537.ko
insmod: error inserting 'Intel537.ko': -1 Operation not permitted
indrek@arvuti:~/proge/intel-2.60.80.1/intel-2.60.80.1$ sudo insmod -f Intel537.ko
insmod: error inserting 'Intel537.ko': -1 Operation not permitted
indrek@arvuti:~/proge/intel-2.60.80.1/intel-2.60.80.1$

I have kernel headers present etc. Wireless is working like a charm :) 
I can always try any other driver, but is nice to know about reasons why things are, as the appear to be :roll: 
So! I`ve tried sudo as well as direct su without luck. Is there any place to go further? Driver belongs to root. Root does not have access to it. Why I wonder...
I have used "linux only" policy 2,5 years now. I simply like understand my equipment. Thats why I also drive very mecanical (non electronic) car. Third party specialists have there own interests, whitch are not always corresponding with my goals ;) 

Perhaps I just try compiling the driver again. I have never seen, that inserting driver needs "chmod". 

Any suggestions???

Indrek

---

