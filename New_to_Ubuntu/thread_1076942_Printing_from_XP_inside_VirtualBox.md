---
title: "Printing from XP inside VirtualBox"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-02-21
I've successfully installed XP SP3 in VirtualBox.  I need to be able to print from XP.  I've installed my printer as default by doing:

[http://10.0.2.2:631:/printers/Deskjet-4200-series](http://10.0.2.2:631:/printers/Deskjet-4200-series)

I selected HP then HP Deskjet, and the printer is showing up as installed and default printer, but won't print anything.  What am I missing, or what am I doing wrong?

---

### Post by theozzlives on 2009-02-21
Authetication

---

### Post by liferules on 2009-02-21
How is the printer connected to the system?

I have a similar setup. I have a Hp C6180 Photosmart connected to my router. I installed a printer (add Printer) to a Standard TCP/IP port at the specific IP address of the printer (192.168.1.100). Works like a charm. That is until the router randomly assigns a new IP address for the printer.

---

### Post by hifly1231 on 2009-02-21
> **theozzlives said:**
> Authetication

What do you mean "Authentication"?

---

### Post by lykwydchykyn on 2009-02-21
Check out these files, and see if you have any errors or messages that look related:
/var/log/cups/error_log
/var/log/cups/access_log

If you're not sure, post them here.

---

### Post by hifly1231 on 2009-02-22
In browsing the Internet, I'm seeing some people recommending printing from VirtualBox using Samba.  How do you do this, and is this the route I should be taking?

---

### Post by lykwydchykyn on 2009-02-23
I wouldn't do it that way.  If regular cups printing isn't working, there's no reason to think samba will.  Samba just adds an extra layer of complexity and permissions issues.

Anything in those log files?

---

### Post by hifly1231 on 2009-02-24
Just in case anyone else is trying to figure this out, I wanted to let everyone know what the solution I found is.  Maybe it'll work for you too.  All I had to do was download the driver for my printer from the manufacturer's website, and it basically set itself up.  Now the printer is all set up, and I can print from inside my VirtualBox Windows XP.

---

