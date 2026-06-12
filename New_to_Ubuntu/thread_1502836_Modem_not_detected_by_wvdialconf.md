---
title: "Modem not detected by wvdialconf"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by ashwani.nair on 2010-06-06
Hi There,

I am trying to configure internet on my newly installed Ubuntu 10.04 (Wubi). I am just a week old to Ubuntu and Linux world.

This is my second thread. With help from ubuntu experts I have tried to configure my Internet, but the problem I am facing is that my modem is not detected.

I did a 'pppconf' to configure the ppp settings, but when I run a 'wvdialconf' it says no modem dected after scanning ports.

When I do a 'lsusb' it does identify my USB modem as ```
Bus 03 Device 02: ID 201e:2009
```.

Modem Info
----------------------------------------
QualComm, Vendor ID: 201e, Product ID: 2009.

Additional Info
----------------------------------------
Ubuntu once detected my modem, at that time, it said
```
Modem Port Scan<*1>: S0 S1 S2 S3
```but now, when I do a 'wvdialconf' it only scans from S0 - S2, it is missing out S3. 



Thanks a lot in Advance.

---

### Post by diablo75 on 2010-06-06
You might check to see if the Hardware Drivers Manager in your System menu shows a driver needing to be enabled in order to use the modem.

You might also try to run "sudo wvdialconf" instead.

---

### Post by gandaran on 2010-06-06
what type of modem is it? mobile broadband or cable dsl? ethernet or usb?
for usb modems install *usb-modeswitch* and *usb-modeswitch data*

---

### Post by ashwani.nair on 2010-06-06
Hi Diablo and Gandran,

Thanks for the response.

I have installed 'usb-modeswitch' and 'usb-modeswitch-data'. Its still not picking up my modem. 

I have tried 'wvdialconf' as well, but its still not picking up my USB Modem.

---

### Post by gandaran on 2010-06-06
> **ashwani.nair said:**
> Hi Diablo and Gandran,

Thanks for the response.

I have installed 'usb-modeswitch' and 'usb-modeswitch-data'. Its still not picking up my modem. 

I have tried 'wvdialconf' as well, but its still not picking up my USB Modem.
have you tried going to the modem manufacturers website to look if they have a linux driver available?

---

### Post by lkraemer on 2010-06-08
Google for "201e:2009 driver" finds:
[http://forum.sabayon.org/viewtopic.php?f=56&t=19229](http://forum.sabayon.org/viewtopic.php?f=56&t=19229)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/490068](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/490068)
(Start reading Posting #7 to the end)
[http://opensource.telkomspeedy.com/wiki/index.php/How_To_Internet_Connection_Using_Haier_CE100_and_Ubuntu_9.04](http://opensource.telkomspeedy.com/wiki/index.php/How_To_Internet_Connection_Using_Haier_CE100_and_Ubuntu_9.04)
[http://priyess-karma.blogspot.com/2010/06/smart-internet-connection-with-modem.html](http://priyess-karma.blogspot.com/2010/06/smart-internet-connection-with-modem.html)
[http://translate.google.com/translate?hl=en&sl=id&u=http://blankblondtank.wordpress.com/2009/09/03/koneksi-internet-smart-dengan-haier-ce-100-cdma-di-linux/&ei=sTgOTKzPLpvsnQfv8dHBDQ&sa=X&oi=translate&ct=result&resnum=3&ved=0CCEQ7gEwAjgK&prev=/search%3Fq%3DHaier%2BUSB%2BModem%2B201e:2009%2Bdriver%26start%3D10%26hl%3Den%26sa%3DN](http://translate.google.com/translate?hl=en&sl=id&u=http://blankblondtank.wordpress.com/2009/09/03/koneksi-internet-smart-dengan-haier-ce-100-cdma-di-linux/&ei=sTgOTKzPLpvsnQfv8dHBDQ&sa=X&oi=translate&ct=result&resnum=3&ved=0CCEQ7gEwAjgK&prev=/search%3Fq%3DHaier%2BUSB%2BModem%2B201e:2009%2Bdriver%26start%3D10%26hl%3Den%26sa%3DN)

Looks as if you need to start with a EJECT of the Storage Drive first, then
config & try the modem.......

lk

---

