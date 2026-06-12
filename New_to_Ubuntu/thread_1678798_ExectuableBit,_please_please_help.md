---
title: "ExectuableBit, please please help"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Ferrus90 on 2011-01-31
Does anyone know how to completely disable this?
I don't mean click the wee box in the permissions tab in the properties menu.
This is for things on a cd, and not a cd/rw.

If anyone could help i'd be most grateful and less likely to scream at/ beat to death with a badger, my flatmate for bugging me for about six months to get rid of windows and install ubuntu

---

### Post by NightwishFan on 2011-01-31
You might have to copy all the files off the cd to a folder if the "no exec" is hard coded in. Not sure.

---

### Post by prshah on 2011-01-31
> **Ferrus90 said:**
> Does anyone know how to completely disable this?

From 10.10 onwards, exe files are handled by /usr/bin/cautious-launcher. You can sudo edit this file and comment out all lines except for the last; but this is obviously a security risk.

A better approach would be to check if the file is on a CD before proceeding; post back if you want code suitable for this.

---

