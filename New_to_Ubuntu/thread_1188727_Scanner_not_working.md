---
title: "Scanner not working"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by Yashaswi on 2009-06-16
Hi,
I am a newbie to ubuntu. I'm currently using ubuntu 8.10...
II'm trying to access my Artec Ultima 2000 scanner. I am getting an error
 failed to open device `gt68xx:libusb:002:002':Invalid argument.
Did chk with the command lsusb
 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:0f0c Hewlett-Packard 
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385/ScanMagic 1200 UB Plus Scanner
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Plz help.......

---

### Post by SteveDee on 2009-06-16
According to the Sane database: [http://www.sane-project.org/cgi-bin/driver.pl?manu=&model=&bus=usb&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=&model=&bus=usb&v=&p=)   your scanner appears to be supported.

Suggest you run System > Administration > Synaptic Package Manager and search on "sane", then try adding any sane related packages.

---

### Post by Mark_in_Hollywood on 2009-07-10
I cannot find help on the net for your predicament. Have you plugged the scanner into a Window/MAC box? Process of elimination can help.

Other than that:

Artec Digital
For Sales Tel: +1-510-897-8900, +1-510-897-8902
For Customer Service Tel: +1-510-897-8902, +1-510-897-8901
For sales & marketing e-mail: [email]info@ultima.com.tw[/email]
For customer service e-mail: [email]service@ultima.com.tw[/email]
Address: 39901 Eureka Dr. Newark, CA 94560

---

