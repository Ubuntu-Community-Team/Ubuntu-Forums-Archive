---
title: "Security issue with windows printers"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by Robotuner on 2007-02-13
I have set up my Edgy laptop to print on two printers located on my windows domain.  I have tries several ways of doing this, and generally have been able to access the printers via Unix LPD, windows smb and CUPS.  It appears that CUPS is the easiest method.  

However, when I look at the CUPS uri connection, the format is :

ipp://smb://domain/user:password@machine/printername

That really is disturbing!  It lists my admin user name and password in plain text!  Are there alternatives to this?

---

