---
title: "need help connecting to my printer"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by contact511 on 2010-06-21
Hi...I have to tell you that I feel really dumb because absolutely nothing on here makes any sense to me.
Anyway...my son loaded ubuntu onto my desktop and took off windows because of the major virus that we had.  Well, now, I can't print from this computer because it's not recognizing he HP printer we have.  Any help you can give would be greatly appreciated.

Also, I have no idea what a thread is or what the list of prefixes are...so I just picked one

---

### Post by sandyd on 2010-06-21
> **contact511 said:**
> Hi...I have to tell you that I feel really dumb because absolutely nothing on here makes any sense to me.
Anyway...my son loaded ubuntu onto my desktop and took off windows because of the major virus that we had.  Well, now, I can't print from this computer because it's not recognizing he HP printer we have.  Any help you can give would be greatly appreciated.

Also, I have no idea what a thread is or what the list of prefixes are...so I just picked one
is the printer directly connected to the pc?

model of the printer?
oh, and try clicking [[URL="apt:hplip,hpijs,hpijs-ppds,hplip-cups,hplip-gui"][here]]("apt://hplip,hpijs,hpijs-ppds,hplip-cups,hplip-gui") [/URL]to ensure the HP printer drivers are installed.

---

### Post by contact511 on 2010-06-21
> **carlee said:**
> is the printer directly connected to the pc?

model of the printer?
oh, and try clicking [[here]]("apt:/hplip,hpijs,hpijs-ppds,hplip-cups,hplip-gui") to ensure the HP printer drivers are installed.

its an hp officejet pro L7680.   I'm not able to click on your link...nothing happens

---

### Post by contact511 on 2010-06-21
> **contact511 said:**
> its an hp officejet pro L7680.   I'm not able to click on your link...nothing happens

Any ideas?

---

### Post by Rasa1111 on 2010-06-21
Hi Contact511~

 I have had trouble connecting lexmark and 'dell' [same thing] printers,
But have not had an issue yet getting an HP printer to connect. 

What version of Ubuntu are you using?

 When I was using Ubuntu 9.10~ My printer worked ok,
but sometimes I would have to turn it off and back on to get working again.

 But in Ubuntu 10.04~ It works perfectly. 

 Is it connected via USB?
If so, is it plugged into a rear USB port?

 What does it say/show when you open "Printers"?
From System>Administration>Printing.
anything?

---

### Post by MyR on 2010-06-21
> **contact511 said:**
> Hi...I have to tell you that I feel really dumb because absolutely nothing on here makes any sense to me.
Anyway...my son loaded ubuntu onto my desktop and took off windows because of the major virus that we had.  Well, now, I can't print from this computer because it's not recognizing he HP printer we have.  Any help you can give would be greatly appreciated.

Also, I have no idea what a thread is or what the list of prefixes are...so I just picked one

**Get your son to help you!** Seriously.

You can also make sure the printer is plugged in, connected to your computer, and turned on. Ubuntu ought to recognize it for you automatically -- it's probably fully supported.

---

### Post by sandyd on 2010-06-21
hmm.
looks like those links don't work in the latest version of ubuntu anymore...
**crys**

getting back..
open system -> administration -> synaptic package manager.

search for, and install the following packages (right click and select "mark for installation") hplip, hpijs, hpijs-ppds, hplip-cups, hplip-gui

then after installing (click apply to install), there should be a "hp" icon in your system tray.
right click it, and select "hp device manager". then click the "+" sign.

if that works, then ill give you the rest of the non-printer steps to make your life easier..

---

### Post by waynefoutz on 2010-06-21
> **contact511 said:**
> Any ideas?


try this link:
[http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")


the wizard on that site, when you navigate to your model printer, and Ubuntu 10,04, it  will lead you here:



> Installation Wizard
You have selected Ubuntu 10.04 using the HP Officejet Pro l7680 All-in-one Printer.

Ubuntu 10.04 supplies HPLIP 3.10.2 and it does support your printer.

As the version of HPLIP supplied with your operating system supports your printer, you may continue to use that version of HPLIP.

You may now optionally download the latest version of HPLIP to get access to new features and bug fixes.


a link to download  hplip, the HP printer driver, will be under the quoted text above.

---

### Post by sandyd on 2010-06-21
> **waynefoutz said:**
> try this link:
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)


the wizard on that site, when you navigate to your model printer, and Ubuntu 10,04, it  will lead you here:
>                              Installation Wizard
You have selected Ubuntu 10.04 using the HP Officejet Pro l7680  All-in-one Printer.

Ubuntu 10.04 supplies HPLIP 3.10.2 and it does support your printer.

[B]As the version of HPLIP supplied with your operating system supports  your printer, you may continue to use that version of HPLIP.
[/B] 
You may now optionally download the latest version of HPLIP to get  access to new features and bug fixes.                      






a link to download  hplip, the HP printer driver, will be under the quoted text above.
not needed, read bolded text

---

### Post by waynefoutz on 2010-06-22
> **carlee said:**
> not needed, read bolded text



> Installation Wizard
You have selected Ubuntu 10.04 using the HP Officejet Pro l7680 All-in-one Printer.

Ubuntu 10.04 supplies HPLIP 3.10.2 and it does support your printer.

As the version of HPLIP supplied with your operating system supports your printer, you may continue to use that version of HPLIP.

**You may now optionally download the latest version of HPLIP to get access to new features and bug fixes.**


Yes, but there is a benefit in doing so...read the bolded text.

---

