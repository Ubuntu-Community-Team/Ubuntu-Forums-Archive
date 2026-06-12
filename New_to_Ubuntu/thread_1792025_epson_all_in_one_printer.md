---
title: "epson all in one printer"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by sean neilan on 2011-06-27
I have Ubuntu 10.04 and I just received a epson  cx 9400 all in one printer but I do not have the disk that contains the drivers I went to epson.com and they do not have drivers that support Linux so I need help to get the drivers and the help on how to install them on my laptop please thank you for your help, I also have a Acer laptop with an Intel p6100.

---

### Post by howefield on 2011-06-27
Did you try here ?

Your printer seems to be listed.

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

---

### Post by sean neilan on 2011-06-27
The web epson tech told me to go to the third party site and I did not know what one I should pick from 32bt 64 bt but I will what you suggested and go from there I am the picture of a complete newby but I am getting it Thank you

---

### Post by SoFl W on 2011-06-28
That is the site I installed my Epson from.
The 32bit or 64bit depends on what version of Ubuntu you installed.  Goto the terminal and type "uname -a" and let us know what it gives you.

---

### Post by sean neilan on 2011-06-28
So cool it worked! Now I know i have  2.6.32-32-generic-pae now that might come in use down the road as I am learning how to operate my OS Thanks a million

---

### Post by nomko on 2011-06-28
It looks like you have the 32-bit version of Ubuntu => PAE kernel is only used when you have more then 3 gig memeory and a 32-bit based version of Ubuntu. You need the i386 deb file.

---

