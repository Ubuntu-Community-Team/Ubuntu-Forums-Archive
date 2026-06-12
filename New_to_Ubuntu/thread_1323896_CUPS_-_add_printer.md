---
title: "CUPS - add printer"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Fenix1 on 2009-11-12
I have HP Laser Jet 1320 printer connected to my usb, and im operating ubuntu server 9.04 or 9.10 not sure. As you probably allready know, this version of ubuntu does not have a GUI so I cant access the web interfacee for CUPS. I,ve tried to add the printer via lpadmin with little success. heres what I get

lpinfo -v

...
direct usb://HP/LaserJet%201320%20series
...

lpinfo -m

...
Foomatic: HP-LaserJet_1320-Postscript.ppd HP Laser Jet 1320 foomatic/Postscript
...


Ok? So then I try to add the printer.

lpadmin -p printer1 -v //HP/LaserJet%201320%20series -m HP-LaserJet_1320-Postscript.ppd
lpadmin: Unable to copy PPD file

I am baffled, what is the problem. I apologize for lack of information. please help.

---

### Post by doug1212 on 2009-11-12
I think cups only listens to localhost by default, so to access web admin interface from lan, the cupsd.conf file will need to be edited to show :

listen xxx.xxx.xxx.xxx:631

Doug.

---

