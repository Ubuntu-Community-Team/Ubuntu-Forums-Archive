---
title: "Printer not working after upgrade to lucid"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by dwhite on 2010-05-11
I get the following status message when i try to print:

/usr/lib/cups/backend/hp  failed

and i cannot print anything

any suggestions?

**Solved (partially) as follows**
go to system-->administration-->printing

highlight the printer in the window that opens, pull down the "printer"menu and choose "properties" (or just double click on the printer icon)

a printer properties window will open, click on "policies" and make sure the "enabled" check box is checked, if not check it.

This seems to work...but i have to keep checking the box, it doesn't remain checked, everytime i print i have to recheck the enabled box to enable the queue, **anyway to make this change permanent?**

---

### Post by ubunterooster on 2010-05-11
go to system>administration>printers. delete the printer and reinstall it.

---

### Post by maxquad on 2010-05-11
I had the same problem I had to go to synaptic package manager and click on and reinstall some of the cups drivers

---

