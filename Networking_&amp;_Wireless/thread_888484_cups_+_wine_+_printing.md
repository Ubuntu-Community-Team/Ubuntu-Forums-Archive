---
title: "cups + wine + printing"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by szedmakt on 2008-08-13
I installed successful the Ricoh Aficio 1045 network printer to my Ubuntu 8.04 with help of:
[http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)   and it's .ppd file.
I use the CUPS admin on:
[http://localhost:631/admin](http://localhost:631/admin)
and here the proper setting is: Device URI: lpd://192.168.1.88/lp

The printer works properly from Ubuntu, but never print from Ubuntu/wine.
We must use the MsWord2003 sometimes under wine.
So, the MsWord shows all of my CUPS printers, but I can't print to any of them. No error message or anything else.

I tried the man pages and the google, too. Only one clue I fond on winehq.com:
Wine still needs the command lpr(from CUPS), when printing a Document.
If I try the lpr command, the error message is:
lpr: lp: unknown printer

My etc/printcap is:
yes:\
:sd=/var/spool/lpd/yes:\
:mx#0:\
:sh:\
:rm=192.168.1.88:\
:mc=0:\
:lpd_bounce=true:\
:rp=text:

and my smb.conf includes:
# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

Can anybody help to find the solution?
(sorry for my bad English... I hope everything is clear above)

---

