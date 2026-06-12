---
title: "ipw2100 + Hoary + WPA doesn't work"
date: 2005-05-06
forum: Networking &amp; Wireless
---

### Post by rflint on 2005-05-06
After 2 days trying to get working ipw2100 + Hoary + WPA i give up.

the hoary kernel module ipw2100 doesn"t have WPA enable. The probleme is explained here :

[http://incognito.shmoo.com/pipermail/hostap/2005-April/010086.html](http://incognito.shmoo.com/pipermail/hostap/2005-April/010086.html)

But i doesn't know hox to solve it (i have tryed to compile wpa2100 but never get WPA enable)

If someone have a solution ... 

Thank you (and sorry for the buggy english)

---

### Post by luca_linux on 2005-05-06
Just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
Note that you have to download the firmware and the driver from [http://ipw2100.sourceforge.net](http://ipw2100.sourceforge.net) and change every string "ipw2200" in the howto to "ipw2100".

---

### Post by rflint on 2005-05-06
Thank you for your help.

I find the solution => in the bugzilla unbuntu !

The tutorial is great (i have use it) but there is a bug in kernel module ipw2100 (last version) so to make everything work you must patch the _crypt.h file ...

I hope this bug will be fix (but for me it's ok).

Thank

---

