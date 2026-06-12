---
title: "Ubuntu 8.04 Windows Shares"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by jeh311 on 2008-05-02
I have set up my networking with windows, and i have created a shared folder in Ubuntu to swap files back and forth for Moding between PCs. The only problem is in Ubuntu i cannot modify those files, but from windows i can. Does anyone know how to remove the permissions.

---

### Post by mikewhatever on 2008-05-02
You can either use <gksudo nautilus> to get root access, or, if that's inconvenient, modify the shared directory's permissions with chmod and chown commands. Check out the how-to [http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html).

---

### Post by jeh311 on 2008-05-03
Thanks there, looks like that may have done the trick.

---

