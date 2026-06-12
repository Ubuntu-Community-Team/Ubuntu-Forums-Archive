---
title: "Smart Label Printer"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Rolfmeister on 2010-04-08
I have been using Ubuntu for some time and love it.  I have a box set up for music on hold and it simply runs forever.  I recently built a new dual core screamer for my home office.  My only issue has been installing a smart label printer, which is a neccesity for an office.  The printer driver from SII loads but does not recognize the printer.  The only one that does is some default Seiko driver in the Ubuntu driver folder.  However, it's a normal printer and the label printer tries to respond, but it all comes out in gibberish, like it's trying to compress an 8.5 x 11 amount of test page data onto a label.....  I've installed every piece of CUPS software known to man and still no luck.  I've tried both default Seiko drivers and both the 200.ppd and 240.pdd drivers from the SII Ubuntu driver download site.  Nothing works with my SLP 240.  Next I'll try the printer on a Windows system to be sure the printer has not gone sour.

But regardless, even if I do get the driver to accept the hardware, what program do you run to manage the labels?  I tried loaidng the SII SLP program for XP using Wine and it is not supported, so what third party program is used to control the SLP? 

Thanks.

---

### Post by albert s on 2010-04-08
what make of printer are you trying to use?
some manufacturers simply do not support Linux/Ubuntu, this is not a fault on ubuntu's part, but on the printer manufacturer, as with a lot of things, if the manufacturer does not support the OS then simply buy/support a manufacturer that does support.

---

### Post by Rolfmeister on 2010-04-08
It's a Seiko Smart Label Printer 240 and the driver is from their site and supports Ubuntu and other deb based Linux distributions.  The error message that comes up when trying to load the proper SII .ppd is "Missing /usr/linexec/cups/filter/seikoslp.rastertolabel program".  I have tried everything and loaded all CUPS filters through Ubuntu.  Even the CUPS site says that CUPS 1.4 supports the Seiko Smart Label Printers.  Any help would be most appreciated.

---

### Post by Rolfmeister on 2010-04-09
I tried the SLP 240 on a Windows PC and it worked fine.  At home Ubuntu gives an error message when installing the .ppd that the header can't be read.  An Adobe issue as I think Ubuntu is confusing the .ppd file as an Acrobat file????  At work it's missing the seikoslp.rastertolabel program, so the .ppd file won't install.  Somethings missing and I can't locate the seikoslp.rastertolabel program anywhere.

---

### Post by albert s on 2010-04-09
Im sorry, Ive never heard of Seiko printers or ever had any dealings with them or even seen one,
so my apologises, but I can be of absolutely no help to you.

---

### Post by albert s on 2010-04-09
just had a look on the site, it doesnt mention what update of Ubuntu is supported,
AFAIK 9.10 has some issues with older drivers for various hardware, may be an idea to e.mail seiko to find out just what Ubuntu support is offered for what version.

---

### Post by Rolfmeister on 2010-04-09
I'll give it a shot.  Seiko and Dymo are the top two label printers on the market, so support should be right around the corner.

---

### Post by albert s on 2010-04-09
ah dymo, yes, I use them myself, but I do that on bluetooth, so it may not matter what OS is being used.
good luck with the seiko though.

---

### Post by oldsoundguy on 2010-04-09
Actually the largest selling stand alone label printer is the Avery personal label printer.  Have one and still have it hung off of a Windows box because nobody gives a **** about trying to write Linux drivers for it.
BUT, having said that, it really doesn't work all that well with Windows either.  Using XP it disappears from the USB printers at regular intervals and the drivers as well as the software package for fonts have to be re-installed.

---

### Post by Rolfmeister on 2010-04-09
Here is the driver install error message when the proper printer .ppd file is chosen: 

PPD Error
Failed to read PPD file.  Possible reason follows:
/home/rolfster/Downloads/SeikoSLPLinuxDriver/siislp240.ppd: FAIL
      **FAIL**  Unable to open PPD file - Missing PPD-Adobe-4.x header on line 0.
                REF: Page 42, section 5.2.

---

### Post by jimmy the saint on 2010-04-09
Here is the openprinting.org page for your printer.  It recommends the SLAP driver.

[http://www.openprinting.org/driver/slap](http://www.openprinting.org/driver/slap)

Here is the download pager for that driver

[http://uutil.tripod.com/slap/](http://uutil.tripod.com/slap/)

---

