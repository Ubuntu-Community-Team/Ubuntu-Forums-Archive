---
title: "how to make Lexmark x6170 printer work"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by aagavin on 2009-01-10
I have a Lexmark x6170 printer but when I plug it in it doesn't print???

---

### Post by nhasian on 2009-01-10
did you add the printer via System->Administration-Printing ?

---

### Post by Temposs on 2009-01-10
It looks like that printer is not supported under Ubuntu's default drivers. 

Upon a cursory search of Google, it looks like someone has been successful in getting this printer to work: [http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/](http://blog.k33bz.com/how-i-got-my-lexmark-x6170-working-on-ubuntu-804/)

BTW, In order to see which printers are supported under Ubuntu, go to System->Administration->Printing->New->Forward

Then choose a manufacturer from the list and click Forward again. You'll see a list of all the supported models. 

Lexmark computers generally suck for running under Linux/Ubuntu.

---

### Post by beezap on 2009-02-21
sudo apt-get install alien libstdc++5 lintian lsb-rpm dh-make  binutils-multiarch libtext-template-perl

tar -xvzf CJLZ55LE-CUPS-1.0-1.TAR.GZ
tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tar.gz
 tar -xvzf install.tar.gz
sudo alien -t z55llpddk-2.0-2.i386.rpm
sudo alien -t lexmarkz55-CUPS-1.0-1.i386.rpm 
sudo tar xvzf lexmarkz55-CUPS-1.0.tgz -C /
sudo tar xvzf z55llpddk-2.0.tgz -C /
 sudo ldconfig

cd /usr/share/cups/model
 sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz 
sudo /etc/init.d/cups restart

Then, plug in the the printer to the usb port, and when Ubuntu finds the printer x6170, change the driver to the z55 ppd file.  Print a test page.

It worked for me.

Edit:  download the driver from Lexmark, just search for z55.

---

### Post by ramjet_1953 on 2009-02-21
A read of this may be useful:

[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X6170](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X6170)

Regards,
Roger :D

---

