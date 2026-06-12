---
title: "Can not connect to networked scanner"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by jonathan-l-harrison on 2013-09-07
HP Pavilion g6 Laptop
Intel Pentium CPU B960
5.8G Ram
x86_64
13.04 raring
Everything is up to date

Epson Stylus Office BX525WD - epson-inkjet-printer-escpr 1.2.3-1lsb3.2 (Seiko Epson Corporation LSB 3.2)
socket://192.168.1.120:9100

I have been trying to scan a document from my wife's laptop on a multi use epson printer/scanner/fax.  I installed xSane, but it fails to find the device on our network.  I can print and I can also find the device fs I type the IP address in to my browser.  I have another PC which I installed xSane on and it works fine.  I have Googled and tried all the suggestions on the forum and other sites, but I just can't get it to work.

Any ideas please.

---

### Post by Merrattic on 2013-09-07
Drivers ?

---

### Post by jonathan-l-harrison on 2013-09-08
Don't know.  I got the drivers from the Epson website some time ago and it prints fine, but I do not know how to tell if I have them for the scanner and if they are the correct ones, and if not where to get them, though as it is an all in one machine, I am assuming that the drivers for the printer must be the same or include for the scanner(?)

Given this is the notice:
[ATTACH=CONFIG]246110[/ATTACH]
1, 2 and 6 I know are OK
3, 4 and 5 I don't know....

What should I do and how?

---

### Post by Merrattic on 2013-09-12
Suggest head back to the Epson website to see what is there, scanner wise. FWIW my Brother AIO has a separate driver for the scanner part.

---

### Post by jonathan-l-harrison on 2013-09-13
Thanks, but did that an age ago. The drivers are all part of a bundled package...

Any othr ideas, please?

---

### Post by Merrattic on 2013-09-14
Well I have just looked on the Epson site and searched for drivers for your model and there are two specific [COLOR=#ff0000]**scanner**[/COLOR] drivers there one for general use and one for the network plugin. Suggest a trip back to collect and try out.

---

### Post by jonathan-l-harrison on 2013-09-15
> **Merrattic said:**
> Well I have just looked on the Epson site and searched for drivers for your model and there are two specific [COLOR=#ff0000]**scanner**[/COLOR] drivers there one for general use and one for the network plugin. Suggest a trip back to collect and try out.
Merrattic
Many thanks for kicking butt....

Sadly tired and it still does not work.

Went to:  [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

It complained about dependencies.  Installed them, but still no joy.

Any further help, please.

PS:  Had to do some other maintenance, which required the use of a CD.  In this case 09:10.  I tried the scanner and it worked in the demo without any issues at all.  So not on,ly does it work on other machines, it also works on this when using the demo CD....  So why not on the installed up to date version?

---

### Post by Merrattic on 2013-09-28
Some printer/scanners need to be setup with a USB connection first, then moved out onto the network. Worth a try ?

---

### Post by jonathan-l-harrison on 2013-10-02
Got to be worth a go, but what I don't understand is that it works fine as a printer.

---

