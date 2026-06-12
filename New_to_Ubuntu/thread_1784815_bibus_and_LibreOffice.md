---
title: "bibus and LibreOffice"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by beew on 2011-06-17
Hi, 

I am trying to install bibus in Natty and it requires OpenOffice writer as a dependency, meanwhile LibreOffice is already installed. What is going on? (I know I can install OOO writer alongside but I hate duplicating programs that are basically the same)

Thanks for any insight.

---

### Post by cariboo on 2011-06-17
You'll probably have to get the latest version from:

 [http://bibus-biblio.sourceforge.net/](http://bibus-biblio.sourceforge.net/)

as the version in the repositories is a bit outdated. You could do a Package Update Request on Launchpad

---

### Post by vanadium on 2011-06-18
This does not fit my experience in Natty. Ubuntu 11.04 comes with Bibus 1.5.1 and thus is up do date. Openoffice is a suggested package, not a dependency. Did you actually try installing bibus from the Ubuntu software center?

---

### Post by beew on 2011-06-18
> **vanadium said:**
> This does not fit my experience in Natty. Ubuntu 11.04 comes with Bibus 1.5.1 and thus is up do date. Openoffice is a suggested package, not a dependency. Did you actually try installing bibus from the Ubuntu software center?

Yeah I did. You can test it out for yourself by trying to install bibus from Synaptic, it will list OpenOffice writer as a dependency to install.

---

### Post by vanadium on 2011-06-19
I did a fresh reinstall last friday, and thus had to install bibus again as well. So indeed, I recently tested this for myself (Ubuntu 11.04 Natty Narwall).
I checked the properties of Bibus, and OpenOffice is mentionned as a Recommended Package, not as a dependency. Thus, you could install Bibus without any of OpenOffice or LibreOffice.

---

