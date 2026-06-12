---
title: "Can't install my printer"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2011-07-13
I have a Dell AIO 946 printer, and Ubuntu seems to recognize the printer fine. When picking the drivers, I just used the recommended settings (generic and plaintext) and it seemed to go fine. However, when it asked me to print a test page, I receive the error:

"CUPS Server Error:

There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

Any ideas why this isn't working?

---

### Post by Matt__ on 2011-07-13
From everything I've heard, and from the searches I carried out, you have a large paperweight with Dell written on it. Sorry.


I suppose you could try some of the other printer drivers and hope something worked, [http://www.openprinting.org/printers/manufacturer/Dell](http://www.openprinting.org/printers/manufacturer/Dell)
but I wouldn't hold your breath.

[HP printers](https://www.amazon.co.uk/CN245B-Photosmart-Wireless--All--Printer/dp/B003OG3PPE/ref=sr_1_7?ie=UTF8&qid=1310582960&sr=8-7) work well and are cheap atm

---

### Post by gdonwallace on 2011-07-13
You might try the web admin for CUPS, it may allow you to install the printer.  In your browser go to [http://localhost:631](http://localhost:631).

At least I am fairly certain that is what it is, I have not used it since trying to install my Cannon MX430, which I have not been able to do yet.

---

### Post by Matt__ on 2011-07-13
> **gdonwallace said:**
> You might try the web admin for CUPS, it may allow you to install the printer.  In your browser go to [http://localhost:631](http://localhost:631).

At least I am fairly certain that is what it is, I have not used it since trying to install my Cannon MX430, which I have not been able to do yet.


Is that mx430 (which I cant find, only LBP-430 printer and mx430 camera) or mx340? the latter which has [U][Linux Drivers]("http://support-au.canon.com.au/P/search?as_q=linux&model=PIXMA+MX340&menu=download&filter=0")
[/U]

---

### Post by Thrashrokz33 on 2011-07-13
Well I guess I'll just go out and buy a new printer then, but I have no idea if it's going to have the drivers for linux, and I doubt that the store clerks will know that either. I'm thinking of getting an HP, are they for the most part compatible with linux? Maybe one for under $50 if they have some. Any recommendations would be great.

---

### Post by Matt__ on 2011-07-13
this is the HP I have [http://ubuntuforums.org/showthread.php?p=11043172#post11043172](http://ubuntuforums.org/showthread.php?p=11043172#post11043172)

HP and lexmark are the best supported. but you can always check [open printing supported list](http://www.openprinting.org/printers)

---

### Post by plucky on 2011-07-13
> HP and lexmark are the best supported. but you can always check open printing supported list

HP = Yes
Lexmark = No

---

### Post by Thrashrokz33 on 2011-07-13
Looks like I found a cheap HP that might work with Linux, but its number was not on the Linux supported printer page. This is the cheapest printer at my local stores.

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=4023245&prodTypeId=18972&prodSeriesId=4023244&swLang=8&taskId=135&swEnvOID=2020](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=4023245&prodTypeId=18972&prodSeriesId=4023244&swLang=8&taskId=135&swEnvOID=2020)

However, it does say support for Linux OS on this page, so does that just mean the Linux support page just doesn't have this one registered? I'm talking about this site: [http://www.openprinting.org/printers](http://www.openprinting.org/printers)

It says on this page that the latest update was around 2007, and I have Ubuntu 11, so does that mean I'll run into problems?

---

### Post by Matt__ on 2011-07-13
that printer will run fine in 11.04 out of the box,
and for additional functionality install [HPLIP]("http://hplipopensource.com/hplip-web/install_wizard/index.html") which will give you the hp-toolbox app.
Its an auto-installer, download and follow the easy to use guide, the .run will install and resolve any issues...I just used it on my hp with 11.04


> **plucky said:**
> HP = Yes
Lexmark = No
dont lexmarks come with the linux logo and drivers ? maybe its just the business ranges and not home user printers.

---

### Post by prabagaar on 2011-08-03
I cant install my EPSON LX 300+II USB printer. where i get the drivers fro this printer

---

