---
title: "Installing the bleeding-edge version of a package"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by darrelljon on 2009-02-03
I know how to use apt and Adept but how do I check the version and install the latest version of a package from the repos? I want to install the latest version of WINE in Kubuntu Hardy.

---

### Post by RomeReactor on 2009-02-03
Hi. You can verify the version installed by opening the Wine configuration program:
```
winecfg
```
and going to the "About" tab.

If you want to install the latest version, [go here]("http://www.winehq.org/download/deb") and follow the instructions; do note, however, this:
> The packages here are beta packages. This means they will periodically suffer from regressions, and as a result an update may break functionality in Wine. If the latest stable release of Wine (currently Wine 1.0.1) works for you, then you may not want to use these beta packages.

I would suggest you keep the version already installed in your system.

---

### Post by blazemore on 2009-02-03
To update to the latest version of wine:

```
sudo su
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - && echo deb http://wine.budgetdedicated.com/apt intrepid main >> /etc/apt/sources.list && apt-get update && apt-get install wine -y --force-yes && apt-get upgrade -y --force-yes
```

---

### Post by darrelljon on 2009-02-03
SOLVED: Thanks, I removed wine and winecfg and deleted ~/.wine directory.
I reinstalled it and it is version 1.1.4 which handles Office 2007 fine except for PowerPoint and OneNote. Also I noticed both Microsoft Office 97 and Microsoft Office 2007 splash screens don't disappear when launching apps so you have to hit return to progress.

---

