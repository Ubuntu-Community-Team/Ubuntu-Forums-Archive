---
title: "Lost my Officejet 6110 after updates"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by DaveM59 on 2009-03-04
I had my Officejet 6110 working fine.  The printer was found and the hplip/hpijs packages were included when I installed Ubuntu.  To get the scanner working, I had to install the hpoj package as well.

This morning I ran updates, rebooted, and now neither the printer nor scanner is working.  Xsane shows the scanner but but reports an i/o error when I try to select it for scanning.  Likewise when I try to print a test page (System/Administration/Printing, right click the Officejet icon and select Properties, then click on print test page) It reports that the page has been sent to the print queue, but the page never prints.  I'm sure this is a driver problem, because the device prints and scans fine in my WinXP system (I have a dual boot setup.)

In Windows I would try removing the device in Device Manager, uninstalling the driver software, then rebooting and reinstalling everything.  In Linux I'm not sure how to proceed.  Help!

---

### Post by ajgreeny on 2009-03-04
What were the updates you installed this morning?  It seems a bit unusual for them to stop your printer working, unless one of the hp packages was updated and was not installed properly.  You could also uninstall the printer from your system and then reinstall it manually, as you would in windows, using the same dialog you did for "Print test page"

---

### Post by DaveM59 on 2009-03-04
Thanks for the reply.  I deleted the printer -- could not figure out how to delete the scanner.  Then I uninstalled hpoj, hplip etc. using Synaptic package manager.  When I rebooted, Ubuntu automatically detected the printer and installed a different driver -- CUPS-Gutenberg.  This restored printer function.  I then reinstalled hpoj, and this also installed the other packages I had removed before (hpijs, hplip etc.).  However, the printer apparently is still using the Gutenberg driver and the scanner is not working.  Should I attempt to change the driver?

EDIT -- I'm not sure I lost the printer because of the updates (5) applied today.  I noticed the loss after this was done, but it may have happened earlier.

---

