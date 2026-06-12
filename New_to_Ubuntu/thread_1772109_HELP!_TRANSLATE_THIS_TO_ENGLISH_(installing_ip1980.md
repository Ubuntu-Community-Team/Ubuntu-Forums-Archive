---
title: "HELP! TRANSLATE THIS TO ENGLISH (installing ip1980 in ubuntu 11.04)"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by 20ronnie69 on 2011-05-31
[B]
[/B]

[B]
[/B]

**Installasi Printer Canon PIXMA iP 1980 di Ubuntu 11.04 **

   
  Adapun langkahnya antara lain sebagai berikut :

Pertama-tama download driversnya di situs canon-europe.
[[http://software.canon-europe.com/products/0010647.asp]](http://software.canon-europe.com/products/0010647.asp])

Selanjutnya Install terlebih dahulu dependensi yang nantinya dibutuhkan sebagai pendukung driver.
$ sudo apt-get install libcupsys2

Kemudian masuk ke direktori atau folder dimana driver yang telah didownload tersimpan. (contoh: di folder Downloads).
$ cd Downloads
$ sudo tar -xf iP1900_debian_printer.tar
$ sudo tar xvzf cnijfilter-common-3.00-1.tar.gz
$ sudo dpkg -i *.deb

Tahapan  Instalasi driver printer telah selesai. Sambungkan Printer ke  PC/laptop/netbook dan sekarang printer sudah dapat digunakan di Ubuntu  11.04.



Untuk **PIXMA iP 2770**:


Dowonload di sini [[http://gdlp01.c-wss.com/gds/0/0100002720/01/cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz]](http://gdlp01.c-wss.com/gds/0/0100002720/01/cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz])


[COLOR=#333333][FONT=verdana]Jalankan:
#tar -zxvf cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz
Kemudian masuk ke direktori hasil ekstrakan tersebut:
#install.sh


this is from this site:
[http://www.yustinus.waruwu.org/2011/05/installasi-printer-canon-pixma-ip-1980.html](http://www.yustinus.waruwu.org/2011/05/installasi-printer-canon-pixma-ip-1980.html)

[/FONT][/COLOR]

---

### Post by jtarin on 2011-05-31
Install Printer Canon Pixma iP 1980 in Ubuntu 11:04


The steps are as follows:

First of all download drivers at canon-europe site.
[[Http://software.canon-europe.com/products/0010647.asp]](Http://software.canon-europe.com/products/0010647.asp])

Next install dependencies first which later needed to support the drivers.
$ Sudo apt-get install libcupsys2

Then go to the directory or folder where the driver has been downloaded is stored. (Example: in the Downloads folder.)
$ Cd Downloads
$ Sudo tar-xf iP1900_debian_printer.tar
$ Sudo tar xvzf cnijfilter-common-3:00-1.tar.gz
$ Sudo dpkg-i *. deb

Stages of the printer driver installation has been completed. Connect the printer to your PC / laptop / netbook and now the printer is to be used in Ubuntu 11.04.



For Pixma iP 2770:


Download here [[http://gdlp01.c-wss.com/gds/0/010000...86-deb.tar.gz]](http://gdlp01.c-wss.com/gds/0/010000...86-deb.tar.gz])


Run:
# Tar-zxvf cnijfilter-ip2700series-3:30-1-i386-deb.tar.gz
Then go to the directory extracted results are:
# Install.sh


this is from this site:
[http://www.yustinus.waruwu.org/2011/...a-ip-1980.html](http://www.yustinus.waruwu.org/2011/...a-ip-1980.html)

---

### Post by 20ronnie69 on 2011-05-31
> **jtarin said:**
> Install Printer Canon Pixma iP 1980 in Ubuntu 11:04


The steps are as follows:

First of all download drivers at canon-europe site.
[[Http://software.canon-europe.com/products/0010647.asp]](Http://software.canon-europe.com/products/0010647.asp])

Next install dependencies first which later needed to support the drivers.
$ Sudo apt-get install libcupsys2

Then go to the directory or folder where the driver has been downloaded is stored. (Example: in the Downloads folder.)
$ Cd Downloads
$ Sudo tar-xf iP1900_debian_printer.tar
$ Sudo tar xvzf cnijfilter-common-3:00-1.tar.gz
$ Sudo dpkg-i *. deb

Stages of the printer driver installation has been completed. Connect the printer to your PC / laptop / netbook and now the printer is to be used in Ubuntu 11.04.



For Pixma iP 2770:


Download here [[http://gdlp01.c-wss.com/gds/0/010000...86-deb.tar.gz]](http://gdlp01.c-wss.com/gds/0/010000...86-deb.tar.gz])


Run:
# Tar-zxvf cnijfilter-ip2700series-3:30-1-i386-deb.tar.gz
Then go to the directory extracted results are:
# Install.sh


this is from this site:
[http://www.yustinus.waruwu.org/2011/...a-ip-1980.html](http://www.yustinus.waruwu.org/2011/...a-ip-1980.html)


thanks for this.... will update latter if the printer is installed and working.

---

### Post by mkornig on 2011-05-31
I don't even recognize the language. What language is it?

---

### Post by s.fox on 2011-05-31
> **mkornig said:**
> I don't even recognize the language. What language is it?

It appears to be Indonesian :)

---

