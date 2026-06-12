---
title: "Internet Navigation"
date: 2005-09-09
forum: Networking &amp; Wireless
---

### Post by albertoramirez on 2005-09-09
Hello, I´m starting my Ubuntu experience, got two problems:

1- I installed a additional Hard Drive as primary slave, and there installed Ubuntu.  The boot manager installed, Ubuntu starts OK, Windows XP (installed in primary master HD) crashes.  Only can start windows in safe mode.

2- I connect to internet throug a cablemodem and a Linksys router via ethernet card.  In win works ok, in Ubuntu, I can´t use Internet.  The card is a CNet Pro200.

Can anybody give me advice?  thanks a lot!!!

---

### Post by Emerzen on 2005-09-09
If you changed any BIOS settings for you hard drive controller before the Ubuntu install, this is likely crashing Windows.  If that's the case, you can reinstall Windows (1st) w/ the new BIOS settings, then setup internet in Windows, then reinstall Ubuntu w/o making further changes to BIOS.  Regarding question 2, I've never had a problem w/ my cable modem, so I don't have any suggestions, hope someone else will be along to help soon.

---

### Post by albertoramirez on 2005-09-09
Hey! Thanks for the answer!

Well, yes, plugged the HD into my computer and did an auto HD detection in the BIOS setup, in order to detect the new HD.

Then, started my machine, checked the new HD in Windows and then, started up it again with the Ubuntu CD in order to install the system.

Ok, thanks!  \\:D/

---

### Post by albertoramirez on 2005-09-09
The gear is...

Cablemodem: Motorola SB5100

Router: LINKSYS WRT54G

Ethernet Card: CNet Pro 200

 :|

---

### Post by albertoramirez on 2005-09-19
Hello there!

Ok, I switched the Ethernet card with an older one and voilá, problem solved.  It was a hardware problem, but only in Ubuntu.  I have a Live rescue CD that starts the computer in Linux with text interface, and it detected the card.

Well, Davicom chips have problems with Ubuntu.

---

