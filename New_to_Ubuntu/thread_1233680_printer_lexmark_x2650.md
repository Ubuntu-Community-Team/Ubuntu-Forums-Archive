---
title: "printer lexmark x2650"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by nene7 on 2009-08-06
hi,
 i have a printer lexmark x2650 and i want to make them work. how i install or how i found the driver.

---

### Post by candtalan on 2009-08-06
this listing might be useful, good luck
[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X2650](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X2650)

---

### Post by nene7 on 2009-08-07
hi, 
in the page of lexmark it support linux but give me some option what are the correct to download:
-desbian GNU/linux 4.0
-desbian GNU/ linux 5.0
-ubuntu 8.04 LTS
- OPEN SUSE 11.0
- Foresigh linux 2.0

---

### Post by halitech on 2009-08-07
Based on the options I would go with the Ubuntu 8.04 version, hopefully it will work with the version you are running.

---

### Post by Magic_Spehar on 2009-09-12
If you're using a 32-bit Ubuntu version then you can find your driver at the Lexmark site.   Try	lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip.  Unzip the file and run the script.  This linux driver certainly works for Ubuntu 8.04, 8.10 and 9.04 [http://support.lexmark.com/index?locale=en&segment=DOWNLOAD&startover=y&userlocale=EN_US&question=x2650&productCode=LEXMARK_X2650&page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_X2650&searchid=1252784030808#1]("http://support.lexmark.com/index?locale=en&segment=DOWNLOAD&startover=y&userlocale=EN_US&question=x2650&productCode=LEXMARK_X2650&page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_X2650&searchid=1252784030808#1")

There's no supported driver for 64-bit Ubuntu versions but there are workarounds. You can find the info on this forum, do a search...

---

### Post by afrodeity on 2010-06-02
The Lucid upgrade appears to have done something to the printer driver, since xsane is no longer recognising the device.

I tried to reinstall the Lexmark 2650 driver which worked with karmic.

Had to sudo the script for it to work.

Now it says I don't have the right cups version 1.2 or higher installed. This used to happen with Hardy, why are we being deprecated, and knocked around just so the Hardy LTS can synch up with the Lucid LTS?

---

### Post by jlamothe on 2010-10-25
I hate to revive a dead thread like this, but ever since upgrading from 10.04 LTS to 10.10, my printer (Lexmark X2650) has stopped working.

I'm using the drivers provided by Lexmark, but they're for 8.04 LTS.  After the upgrade, I uninstalled them, reinstalled them and rebooted just in case the upgrade process did something, but I still get nothing.

The printer shows up as you would expect, but whenever you send a print job to it, it just sits in the spooler forever.  Has anyone else experienced this and found a workaround?

---

### Post by afrodeity on 2011-06-06
[http://ubuntuforums.org/showthread.php?t=1223710](http://ubuntuforums.org/showthread.php?t=1223710)

---

