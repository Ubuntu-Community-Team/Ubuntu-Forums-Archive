---
title: "Cant install tar.gz files"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by TimEnid on 2010-07-26
i downloaded a theme and extracted its contents to my desktop. next, i opened a terminal and typed in "tar -xzvf Ambience-x-mint.tar.gz" but then i get this message:
tim@tim-desktop:~$ tar xzvf Ambiance-X-Mint.tar.gz
tar: Ambiance-X-Mint.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

any suggestions. thanks.

---

### Post by wojox on 2010-07-26
If it's a theme open Appearance and drag and drop your .tar.gz file.

---

### Post by flick on 2010-07-26
Case sensitivity :

Ambience-x-mint.tar.gz

vs

Ambiance-X-Mint.tar.gz

---

### Post by oldos2er on 2010-07-26
"tar: Ambiance-X-Mint.tar.gz: Cannot open: No such file or directory"

 If Ambiance-X-Mint.tar.gz is on your desktop, you'll need to run **cd Desktop** first. But there's usually no need to extract a theme, just drag the tar.gz file into the Appearance app (System, Preferences, Appearance, Theme tab). [https://help.ubuntu.com/community/UbuntuEyeCandy#Desktop%20Themes](https://help.ubuntu.com/community/UbuntuEyeCandy#Desktop%20Themes)

---

### Post by TimEnid on 2010-07-26
> **wojox said:**
> If it's a theme open Appearance and drag and drop your .tar.gz file.

thanks a lot

---

### Post by wojox on 2010-07-26
Your Welcome. :D

---

