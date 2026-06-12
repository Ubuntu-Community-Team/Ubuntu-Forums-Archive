---
title: "Is there a Linux printer driver for Dell Photo 944?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by bwallum on 2009-04-30
Hi 

I have just sorted a Windows virus by installing Jaunty, running clamav and zapping the nasties in the Windows directories. It has been so successful that my friend wants to keep using Ubuntu.

One small snag, her printer is a Dell Photo 944. It is an all in one with copier,fax, scan and printer functions.

I have tried a standard printer install from System>Administration>Printing, the printer appears to be recognised but there is no driver for it. I am offered other drivers for Dell models 1100, 1110, 3100cn, M5200, S2500. I have tried 1100 driver but it does not work. 

How can I get this printer working please?

---

### Post by halitech on 2009-04-30
Is it the Dell All in One photo printer?

if it is, bad news, its a paperweight in linux.
[http://openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Printer_944](http://openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Printer_944)

---

### Post by starcannon on 2009-04-30
Looks like that printer is not gonna work :( as the link Halitech gave.

However, HP printers work beautifully; indeed I have not had an HP yet that would not work, I currently use a C4385 (uses the C4380 driver) and it works perfectly, all functions.
My dad has an HP All in One with Fax that completely works with Ubuntu as well.

My advice, if you can swing it, is get an HP, be sure to make a list of the printers your interested in, then check here in the forums or check it against [this database]("http://www.openprinting.org/printer_list.cgi"). Good luck and have fun.

Other useful printer links for Ubuntu:
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)
[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)
[http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)
[http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi)

---

### Post by LowSky on 2009-04-30
From what I remember Dell uses rebadged Lexmark printers. Lexmark has nearly zero Linux support. Sorry your just out of luck as this link suggests

[http://www.openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Printer_944](http://www.openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Printer_944)

---

### Post by Sef on 2009-04-30
Best thing to do without buying a new printer is buy a old P3 with XP and make it a print server.

---

### Post by dawiba on 2009-04-30
You could try this:

With the printer plugged in/ switched on etc.,

System -> Administration -> Printing -> New

You should now be able to see your printer, if so, select it.

Click the Forward button.

Choose Generic and click the Forward button.

Now choose Postscript Printer and then click the Forward button.

Name your printer and so on in the next screen, then click apply.

---

### Post by veal on 2011-08-17
> **dawiba said:**
> You could try this:

With the printer plugged in/ switched on etc.,

System -> Administration -> Printing -> New

You should now be able to see your printer, if so, select it.

Click the Forward button.

Choose Generic and click the Forward button.

Now choose Postscript Printer and then click the Forward button.

Name your printer and so on in the next screen, then click apply.

Did anyone try that for this printer? Did that work?

---

### Post by aeiah on 2011-08-17
> **Sef said:**
> Best thing to do without buying a new printer is buy a old P3 with XP and make it a print server.

or buy a print server that doesnt ruin your electricity bill

---

