---
title: "Installation of .deb files - AVG"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by msimon1960 on 2009-10-13
I'd like to install AVG Free for Linux to evaluate the package.

I'm using Ubuntu 9.04.

I've downloaded the .deb package to my desktop.

I can't open the .deb package with Gdebi Package Installer to install the software.  Appears to be a security restriction (Oy vay!).

Has anyone installed AVG Free 8.5 on Jaunty yet?

Matt.

---

### Post by spcwingo on 2009-10-13
What errors are given when installing from the terminal?

First open a terminal and change to the directory that the deb file is in:

```
cd /path/to/deb
```

To install from the terminal input this command:

```
sudo dpkg -i NAME_OF_PACKAGE.deb
```

---

### Post by oboedad55 on 2009-10-13
> **msimon1960 said:**
> I'd like to install AVG Free for Linux to evaluate the package.

I'm using Ubuntu 9.04.

I've downloaded the .deb package to my desktop.

I can't open the .deb package with Gdebi Package Installer to install the software.  Appears to be a security restriction (Oy vay!).

Has anyone installed AVG Free 8.5 on Jaunty yet?

Matt.

I've got it installed and running, although I wonder why I bother with it.

---

### Post by msimon1960 on 2009-10-14
Thank you SPCWINGO!

It installed fine using your instructions.  I had used the gDebi Installer that is standard but it doesn't prompt for root access for installation.

I'll find out who to report this to for the next fix.

---

