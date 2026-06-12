---
title: "asking to manually run dpkg --configure -a"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by ajaywilliambrown on 2009-07-13
asking to manually run dpkg --configure -a how do i do this, also when i try to run normal or extra visual efects it says desktop effects could not be enabled, please help i would really apreciate it thanks

---

### Post by lisati on 2009-07-13
You need to run the command from the command line, which you can access on the Applications->Accessories->terminal.
Type in (or copy) the command:
```
sudo dpkg --configure -a
```
You'll be asked for your password. Don't worry if it doesn't show as you type, this is a normal Ubuntu security precaution: type in your password as usual. 

Good luck.

---

