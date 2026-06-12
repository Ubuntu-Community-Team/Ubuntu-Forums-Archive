---
title: "Unable to Detect Scanner in Lexmark x2630 all-in-one Printer in 64-bit Ubuntu 10.04"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-05-08
Hi Guys

I am fairly inexperienced user currently running Ubuntu 10.04 LTS 64-bit. I am trying to get a Lexmark x2630 Printer/Scanner combo to work.

I downloaded the Linux driver from the Lexmark website, which is only for 32-bit. I browsed a whole bunch of forums online, and was able to find instructions to force 32-bit architecture and successfully run the installation program through terminal.

Now the printer works just fine. I am able to print without any issues at all. It's the scanner I am unable to get Ubuntu to detect. Neither Xsane nor SimpleScan detect it. I tried a few solutions offered on some forums, such as downloading the cc548.fw file etc. Got nothing so far.

Looking at the forums and responses to solutions, it also doesn't seem like the issue has been solved for 64-bit users.

I would appreciate any help you can offer.

Thanks.

---

### Post by seventhsamurai on 2010-05-08
FYI, the 32-bit Installation file is self-executable. It runs, but aborts during installation, obviously as it is incompatible with 64-bit architecture.

[Here is the link to the file]("http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2630&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_US&locale=en")

---

### Post by hansdown on 2010-05-08
> **seventhsamurai said:**
> FYI, the 32-bit Installation file is self-executable. It runs, but aborts during installation, obviously as it is incompatible with 64-bit architecture.

[Here is the link to the file]("http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2630&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_US&locale=en")

Hi seventhsamurai.

 Lexmark seems to give and take on their drivers. 

I haven't found a 64bit driver.

---

### Post by wilee-nilee on 2010-05-08
Try simple-scan install from synaptic it is a generic scanner device, there is also xsane installed already in accessories-graphics.

---

### Post by seventhsamurai on 2010-05-08
Like I said in my first post, tried both Simple Scan and Xsane. Neither reads it.

---

### Post by wilee-nilee on 2010-05-08
> **seventhsamurai said:**
> Like I said in my first post, tried both Simple Scan and Xsane. Neither reads it..)

Sorry my bad, ;)

---

### Post by seventhsamurai on 2010-05-09
Still trying to figure this out? Any takers? As of now, I'm printing out of Ubuntu, and turning on a windows virtual desktop with the windows drivers if I want to scan. So yes, I am able to work it on the same computer, but in an ideal world, I wouldn't have to use the virtual desktop.

---

### Post by Jimoid on 2010-05-14
Hi seventhsamurai,

I have the same problem (64 bit 10.4 and a x2650 printer/scanner) but couldn't get the print driver to install. The install complains about CUPS version being <1.2, where it is really 1.4.3. How did you force the install?

Like you I am going to have to use a VM to scan until I can find a way to drive it through Ubuntu.

Cheers

---

