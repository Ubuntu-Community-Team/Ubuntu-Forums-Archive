---
title: "plase help with ndiswrapper"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by Tomas Galli on 2006-08-02
I´m traying to install ndiswrapper. i´m following the instructions from many places. 
this is what i'm doing

1)download and unpack ndiswrapper
2)uname -r (to see my kernel) Is 2.6.15-26-386
3)download the linux-2.6.15.tar.bz2 kernel source (i think is the one i need, i don find one         called exactly like my kernel:2.6.15-26-386
4)unpack linux-2.6.15.tar.bz2 in /usr/src
5)make a simbolic link with
   sudo ln -s /usr/src/linux-2.6.15  /lib/modules/2.6.15-26-386/build
6)go to /home/m y n a m e/modules/ndiswrapper (here was where .tar.bz2 file automatically extracted in)
7)and then 
 sudo make (i made aldo sudo make install)
  
and this is what i get:

Can't find kernel sources in /lib/modules/2.6.15-26-386/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make: *** [prereq_check] Error 1

Please help

I nee ndiswrapper to install windows drivers for my Nexxt usb wifi adapter. It have the sis163U chipset


Thank´s and sorry my english (cheers from argentine)

---

### Post by Banewood on 2006-08-03
You are probably going about it the hard way.  Unless you are doing something really different with the recent version of Ubuntu that you are running, why don't you just get the ndiswrapper BINARY and run that?

---

### Post by steveob on 2006-08-04
Try "sudo apt-get install ndisgtk".  Just worked for me and installed ndiswrapper and all dependencies.  Good luck.

---

### Post by Tomas Galli on 2006-08-05
Thank&#347; u both for answsering. I,m working so hard at the momet on another things,, i&#314;l try what u are saying and i&#314;l tell u


Thank&#347; again

---

