---
title: "Can't print to Windows-shared printer"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by dwhitney67 on 2009-01-05
Hi,

I can't figure out why I am unable to print from my Linux machines (one is Ubuntu 8.04, the other Fedora 9) to a WinXP system that has a shared printer.

On the WinXP system, I am able to see that print jobs sent from the Linux machine are received, however nothing prints.  In fact, the printer, which is an HP Deskjet F300, exercises its servo and then just sits their quietly with the light blinking next to the power button.

The firewall on the WinXP system has been (temporarily) disabled; on the *nix systems, I am using CUPS.  I set the printers on the *nix systems as Samba driven (smb:://MSHOME/PLUTO/Printer).

On the WinXP system, I can monitor the print-spooler of the printer.  As stated earlier, I can see the jobs being posted, however nothing prints.  When I attempt to print from WinXP, the printer behaves nicely.

Does anyone have an idea what is going on?  Is this a CUPS problem?

---

### Post by bhold on 2009-01-06
Sounds similar to a problem I have had in the past, try this.

On the XP system, printer properties / ports...
make sure the Enable bidirectional support box is NOT checked.

---

### Post by dwhitney67 on 2009-01-07
That was it!  Thanks a lot.  It's amazing such a simple solution evaded me for so many hours.  It never occurred to me to look on the Windows side.

---

