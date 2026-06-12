---
title: "Reset Boot after uninstall"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by axxamax on 2009-10-24
I've just tried Ubuntu 9.04 but currently have too many problems for the time I have available. I have uninstalled it but I am still offered the option of Ubuntu when I boot up the computer. I had installed "inside windows" if this makes any difference

---

### Post by DezSP on 2009-10-24
Look for the boot.ini file in the root of your Windows partition (i.e. C:\boot.ini). This contains a list of bootable operating systems, one of which will be Ubuntu. Simply remove the offending line from the file and it should disappear on your next reboot.

If you run into any problems with the bootloader, you can use a Windows installation CD to reach the recovery prompt, then enter the command "FIXMBR" to sort out any problems.

---

### Post by axxamax on 2009-10-24
Managed to sort it by using System restore.

---

