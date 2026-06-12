---
title: "uninstalling dual boot ubuntu"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by PC4 on 2010-11-13
How do I uninstall Ubuntu 10.10, dual boot with Windows XP 64bit Pro? There is no program to unistall in Windows Control Panel, WUBI I believe it is known as.

---

### Post by Paqman on 2010-11-13
If you installled Ubuntu using Wubi, then you can uninstall through Windows Add/remove Programs.

If you installed from a CD, then you can just delete the Ubuntu partition (use the Ubuntu Live CD or the Windows partition editor) then boot Windows into Recovery Mode and run [fixmbr]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx").

---

