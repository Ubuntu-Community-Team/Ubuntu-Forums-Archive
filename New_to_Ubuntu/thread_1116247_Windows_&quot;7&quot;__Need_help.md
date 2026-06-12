---
title: "Windows &quot;7&quot;  Need help"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Pal369 on 2009-04-04
Greetings, just installed Ubuntu with wubi on to my spare pc that I use with Windows 7. After installation and the reboot, it will not give me a boot option, it goes right into the windows 7.

Is there a solution?

Thank you

---

### Post by ibuclaw on 2009-04-04
Windows 7 is not yet fully supported by Wubi on the Ubuntu 8.10 and earlier versions.

There are workarounds, however. Please consult this page for details:[https://bugs.launchpad.net/wubi/+bug/318135](https://bugs.launchpad.net/wubi/+bug/318135)

Regards
Iain

---

### Post by jamesrfla on 2009-04-04
Maybe Wubi is not compatible Windows 7 yet but that would be odd.

---

### Post by ibuclaw on 2009-04-04
> **jamesrfla said:**
> Maybe Wubi is not compatible Windows 7 yet but that would be odd.
No, it is compatible ... it's just the way the Wubi scripts work.

It runs a case statement for what OS it is running under, and since Windows 7 isn't in the list of OS's to match, it fails to set itself up on the bootloader config file.

Regards
Iain

---

