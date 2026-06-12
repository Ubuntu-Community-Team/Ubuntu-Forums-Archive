---
title: "Brother DCP-150CPrinter/scanner"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Chatterton on 2009-01-09
On Ubuntu 8.04 lts.Printer /scanner Brother DCP-150C .Prints OK .Scanner the problem.Brother have been helpful but have a snag.When I attempt as advised to go to "/etc/udev/rules.d/40-basic-permissions.rules" file to edit "USB devices"section Iam informed that I have no authority. Any suggestions .Am new to all this .Is this the right place to ask this question.

---

### Post by SafeFromWindows on 2009-01-09
Try from Console: sudo /etc/udev/rules.d/40-basic-permissions.rules

---

### Post by plucky on 2009-01-09
> **SafeFromWindows said:**
> Try from Console: sudo /etc/udev/rules.d/40-basic-permissions.rules


That command will not do anything as there is no "gedit" in the command.
Try ```
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules
``` will give you the necessary permissions to edit that file after you enter your login password.

Good Luck

---

### Post by Chatterton on 2009-01-10
Thank you Plucky it worked perfectly.Chatterton

---

