---
title: "[ubuntu]Brother MFC-255CW Printing problem"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by mom2twinzz on 2010-05-13
I have tried just about every idea to get this darn printer working.  Most threads seem to be from a couple of years ago, so I know the problem has been solved before.

Basics: Ubuntu Lucid fully updated and Brother MFC-255CW Printer through network connection

1st Try: Brother drivers from Software Center, installed both common and extra Cups and LPR drivers.  Printer was appearing in CUPS but would fail on printing.  Edited configuration to use ip address instead of named server. Still nothing.

2nd Try: Installed drivers from Brother website, following all directions.  Printer appeared as a USB printer.  Fixed per instructions on Brother website.  This time I get the data to go through and everything appears okay in CUPS but nothing actually prints.  I have had to resort to using VirtualBox and moving files that way to the printer using a windows driver.

:confused:I would appreciate any ideas on how to troubleshoot the problem as I assume it is because the data is not actually transmitting to the printer.

>> Fix?  Apparently once I installed samba, apache2.2-bin, and libapache2-mod-dnssd the printer began working.  I had to install those to allow the share from my laptop to the windows box, for my dh who has yet to learn linux.

---

