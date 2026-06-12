---
title: "Re HP printer"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Darr1 on 2010-05-22
I.d really appreciate some help! I'm a complete beginner and recently installed Ubuntu 10.04. I've also installed HPLIPS from a command line. I can open up the HP device manager and it detects my F2400 series printer. I can also find the necessary driver file but when I go to 'Add new printer' I,m told that CUPS is not running and has to be started.
I then used the command line: sudo /etc/init.d/cups start. I then get: Starting Commom Unix Printing System CUPSD.  Warning: Fake start-stop-daemon called, doing nothing.
Is there anything I can do?

---

### Post by bumanie on 2010-05-22
I once had a similar issue and cured it by uninstalling the printer and then reinstalling it. Alternatively, go to the HP linux site and download the latest linux universal installer and try that.

---

