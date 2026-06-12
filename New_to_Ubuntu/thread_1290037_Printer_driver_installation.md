---
title: "Printer driver installation"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by AliSajidImami on 2009-10-13
Hello every one.
I'm having a little problem. I have a printer Canon LBP2900 and UBUNTU doen't recognize it. I have found a driver for it but it is .rpm, and i don't know how to make red hat installers work here. Is it possible?

---

### Post by wojox on 2009-10-13
Try this: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

---

### Post by mapes12 on 2009-10-13
alien may be able to help you out. You can install it from Synaptic:

[http://amitech.50webs.com/installing/index.php.html#rpm](http://amitech.50webs.com/installing/index.php.html#rpm)

[http://www.icewalkers.com/Linux/Software/57020/Alien.html](http://www.icewalkers.com/Linux/Software/57020/Alien.html)

---

### Post by AliSajidImami on 2009-10-13
Thanks!

---

### Post by AliSajidImami on 2009-10-15
I installed the driver. Ubuntu now detects the printer and installs it, but when i try printing a test page, it prints nothing. I can see the page in the queue but the printer sits motionless. what am i doing wrong?

---

### Post by AliSajidImami on 2009-10-16
Also, i tried printing an image, and the queue says it is done but it was not printed. Help please?

---

### Post by mosaic2s on 2009-10-16
try CUPS.

I use Canon LBP 1210 on ubuntu 8.04 LTS. It works fine through network. But only after CUPS drivers were installed.

Let me know if you are able to find the link for CUPS printer drivers.

---

### Post by AliSajidImami on 2009-10-16
The drivers are already installed. The ones i downloaded from Canon website.
Can't find any CUPS drivers.

---

### Post by aljoriz on 2009-10-16
Hope this helps:

goto System>Administration>Printing
click on the printer>properties>printer options

make sure that that printout mode is the same with the kind of ink you have installed on the printer. 
I.E. If you only have a black ink on the printout mode be sure to select BLACK CARTRIDGE

---

### Post by AliSajidImami on 2009-10-16
> **aljoriz said:**
> Hope this helps:

goto System>Administration>Printing
click on the printer>properties>printer options

make sure that that printout mode is the same with the kind of ink you have installed on the printer. 
I.E. If you only have a black ink on the printout mode be sure to select BLACK CARTRIDGE

Did the above.
Nothing happened.
It keeps saying "processing" in the queue:(

---

### Post by mosaic2s on 2009-10-17
Sorry about memory mismatch.
I had downloaded and installed CAPT drivers.
The link suggested earlier in the threat shld work.

Try disconnecting printer and re-connecting to USB port - let ubuntu detect the new hardware and proceed from there.



	 		**Re: Printer driver installation**
 		Try this: [https://help.ubuntu.com/community/Ha...Canon_LBP_2900]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900")

---

### Post by AliSajidImami on 2009-10-18
Didn't work :-(

---

