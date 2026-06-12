---
title: "Boot Problems"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by mesmith on 2009-04-24
About one in eight cold starts results in a hang at "checking battery status".  I'm running a desktop, Dell Dimension 3000, P4 dual processor.  No battery.  User manual indicates Power Management as APM.  I unchecked the ACPI Servies entry, but don't get any improvements.  Googled the problem and found advice to add acpi=off to the Grub menu at the kernel line, right after "ro".  All that did was break my Wireless connection, so backed out that change.  Anybody know a nooby fix for this problem?  I can live with the boot problem if I have to, but would like a fix.  Otherwise, I'm very hapy with Xubuntu 8.10.  No other problems.

---

### Post by mesmith on 2009-04-25
A little more investigation reveals that the Dell is at least partially compliant with acpi standards.  So, I have turned off the apm service and turned on acpi.  Perhpas some conflict will be eliminated.  Will post back if problem resolved.

---

