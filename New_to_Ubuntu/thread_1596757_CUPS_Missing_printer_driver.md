---
title: "CUPS: Missing printer driver"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by barrys2010 on 2010-10-14
Hi, I've used ubuntu on and off since version 7.10 for general use. I just tried installing my printer "Epson Stylus NX420", I found the .ppd file for it online and found the correct CUPS filter. I copied the filter to "/usr/lib/cups/filter" and changed the owner and permissions for the file. After a restarting cups I am still getting the "Missing Printer Driver" error. 

Any suggestions?

System: Ubuntu 10.10 32-Bit

---

### Post by anglican on 2010-10-14
> **barrys2010 said:**
> Hi, I've used ubuntu on and off since version 7.10 for general use. I just tried installing my printer "Epson Stylus NX420", I found the .ppd file for it online and found the correct CUPS filter. I copied the filter to "/usr/lib/cups/filter" and changed the owner and permissions for the file. After a restarting cups I am still getting the "Missing Printer Driver" error. 

Any suggestions?

System: Ubuntu 10.10 32-BitInstall the driver from:

[http://avasys.jp/eng/](http://avasys.jp/eng/)

H

---

### Post by aust77 on 2010-10-14
I'm not sure if I'm understanding you're issue correctly, but why not search for your CUPS driver in Synaptic Package Manager? After several releases of getting ppds off of Brother's website I found a package that had the CUPS wrapper for my HL-2040 in Synaptic.

---

