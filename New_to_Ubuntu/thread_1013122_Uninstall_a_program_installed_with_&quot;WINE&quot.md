---
title: "Uninstall a program installed with &quot;WINE&quot;"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by sharbeloun on 2008-12-16
I installed Winamp on Ubuntu8.10 using WINE and now am trying to unistall it .. i cant find it in ( Application > WINE > Programs .. ) 

where i can find it to Uninstall it ?

---

### Post by DOS4dinner on 2008-12-16
In the wine menu under applications, you should find "Uninstall wine software"

Applications>Wine>Uninstall wine software

If that fails, go to Wine's fake C:\ drive and delete its folder.

---

### Post by Hospadar on 2008-12-16
just type ```
uninstaller
``` in a terminal or Alt-F2 prompt.
Also, if that's the only thing you have installed, you can just delete your .wine directory (this would delete any wine settings you have)

---

### Post by markharding557 on 2008-12-16
you can also uninstall win apps from wine by using the programs uninstaller in its directory in the wine folder

---

