---
title: "Ubunter Server - network setup failing during install"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Simon Tregear on 2010-12-04
Hi All,

I am trying to install 10-10 Server 32 Bit and cannot get the network working.

I've had a LAMP server running ubuntu for a couple of years without problem, but it was attcked via the mail server and when I unstalled that, was then attacked through Port 80 on phpMyAdmin.  I am pretty much a Linux novice and I suspect I hadn't locked surgemail down properly or installed php in a secure place.

Because the log files showed some files had been uploaded and new users added, I decided a clean re-install would be sensible.

I downloaded an iso image and created a boot CD.  The CD starts up okay, and when it comes to detecting network cards, it always suggests the card not plugged into my internal network switch.  I change the selction and follow the prompts and set up with a static IP address as I had them previously.

However, the install doesn't retrieve the time from the Internet, and APT-Get retreive seems to fail.  On completion of the install, I can't ping any IPs - not even internal addresses, and other machines on the internal network can't ping the server either.  I've tried both network interfaces and tried having the cable disconnected prior to network setup.

Given the machine has been working perfectly until I decided to start the clean install, I think it must be something I'm doing wrong.

A possible issue - I run SmoothWall as my firewall and currently all ports are closed, but the server static IP address has been provided permission to access the Internet.  Do any ports need to be open for an Install?

Any help thankfully received.

Simon.

---

### Post by Simon Tregear on 2010-12-08
Resolved.

After research here and in other places I uncovered a number of references to release 10.10 being unstable and buggy.

Downloaded Server 10.04.1.  It installed perfectly first time.  Network came up immediately and following install of other software and several reboots appears fine.  :D

---

