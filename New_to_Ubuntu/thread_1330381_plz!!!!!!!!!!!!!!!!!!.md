---
title: "plz!!!!!!!!!!!!!!!!!!"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by nayeem007 on 2009-11-18
when upgrading to 9.1 it says

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'kubuntu-desktop' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

plz...........advise

---

### Post by NightwishFan on 2009-11-18
Open a Konsole windows and type this command:
```
sudo apt-get update && sudo apt-get -f install
```

If the command asks for your input and tells you to remove packages, please post what packages here before you say "yes" to the command.

---

### Post by ukripper on 2009-11-18
I hope you have made backups for important data before upgrading to 9.10. i would still recommend clean install of 9.10.

---

