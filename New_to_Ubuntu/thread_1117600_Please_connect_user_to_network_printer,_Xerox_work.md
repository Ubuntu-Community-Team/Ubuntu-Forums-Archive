---
title: "Please connect user to network printer, Xerox workcentre 7232 PCL 6."
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Tylor on 2009-04-06
plese help!

---

### Post by MrWES on 2009-04-06
> **Tylor said:**
> plese help!

First of all, is the printer shared on the network PC? What OS is the shared printer running on? We need more information before we can help you. :)

Bill

---

### Post by tarps87 on 2009-04-06
How far have you got? What have you tried so far?
The printer app is under system -> administration -> printers
What version of Ubuntu are you using?

---

### Post by halitech on 2009-04-09
download the PPD files for this machine at: [http://www.support.xerox.com/go/getfile.asp?Xlang=en_ZA&XCntry=ZAF&objid=61334&EULA=0&prodID=WC7232_WC7242&Family=WorkCentre&ripId=&langs=English&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_ZA&XCntry=ZAF&objid=61334&EULA=0&prodID=WC7232_WC7242&Family=WorkCentre&ripId=&langs=English&plats=Linux&Xtype=download&uType=)

Extract the files and then go through the install for the type of connection you have (ie. shared, direct connect to network) directing it to use the PPD file you downloaded and extracted.

---

### Post by serig on 2011-10-18
Hi. I have the same problem with workcentre 7232 and my ubuntu 11.10. I've found it on the network: SuperKey -> printers. I've tried to install automatically (found it but doesn't print documents), manually choose drivers (same), tried to install PPD files from previous post(doesn't work). Please help to resolve this problem.

---

### Post by muzah on 2011-12-06
I actually have the same problem here with UBUNTU ONEIRIC 11.10 and a workcentre 7232 through wifi/ethernet connection.

Every steps of the install process work fine - found a prop. XEROX driver, install it and the printer seems to be OK with the appropriates options.

BUT nothing works or sometimes there is an error with helvetica font.

Please we need help :confused:

---

### Post by martin_h on 2012-06-12
Did anyone ever solve this problem ? I am struggling with the same under 11.04 and after two days no solution. If I try to install from terminal I get: ERROR: can't open file, XeroxInstall/disks 

There is no folder XeroxInstall so it seems the script in setup is wrong.

Anyone an idea ?

Martin

---

### Post by oldos2er on 2012-06-12
Old thread closed. Please start a new thread for your question.

---

