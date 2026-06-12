---
title: "IS HP really compatible with Ubuntu?"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by Irish1 on 2010-10-28
Hello,

I have recently gone from a Lexmark to an HP Officejet J4580 printer.  I needed a new printer and since I have Ubuntu I thought an HP Printer would be a good fit.  I have found the driver for the J4500 series and everything looks good - printer is enabled, etc., but the print job only says processing and then pending and nothing else happens.  I have managed to print items in Windows.

Any thoughts?

---

### Post by MrRichard on 2010-10-28
Just a few minutes ago, I was able to install my Brother MFC 7220 printer. It's an excellent laser printer/scanner and faxer. What I did was went on to the manufacturers website, download the drivers and used CUPS to install the drivers.

Or, you may get lucky by going to System->Administration->Printing and add a printer. Follow the steps and let CUPS search for the appropriate driver and install it, unless you have a PPD driver file or it can't find your printer.

Hope this helped. :guitar:

---

### Post by jonnywombat on 2010-10-28
HPLIP is the driver and utility suit from HP for linux. You can install it via the software centre. For a printer like yours which has been around for a while then that should work fine. 

However if that is giving you problems then you can download and install from the HP website. 

I have gone through there site and can confirm [this driver]("http://hplipopensource.com/hplip-web/index.html") should work just fine. 

Follow the instructions on the linked page for installation instructions.

---

