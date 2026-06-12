---
title: "completely uninstall software?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by slacker9876 on 2009-01-16
Hi I am trying to remove postfix though the series of:

sudo apt-get remove postfix
sudo apt-get autoremove
sudo apt-get purge postfix

All seems to go well, but when I try to re-install postfix I do not get the wizard that allows me to choose what kind of postfix I want i.e., Internet Host, Smarthost with Relay, etc.

What do I need to do to actually remove the package so the system is not aware it was ever installed?

---

### Post by HotShotDJ on 2009-01-16
> **slacker9876 said:**
> What do I need to do to actually remove the package so the system is not aware it was ever installed?The correct command to accomplish this is```
sudo apt-get autoremove postfix --purge
```I hope that helps!

EDIT:  Some software has user-specific configuration files that are written to the user's account -- for example .package_name (it could be just a file, or it could be a folder that contains the configuration files).  I don't think postfix has user-specific files, but if it does, you'll want to manually remove those.

---

### Post by LowSky on 2009-01-16
go to your home file, hit Ctrl+h to see hidden files, find the folders for postfix and delete it.

now reinstall postfix

---

### Post by binbash on 2009-01-16
sudo apt-get purge postfix is the best.I do not recommend autoremove with apt-get

---

### Post by HotShotDJ on 2009-01-16
> **binbash said:**
> sudo apt-get purge postfix is the best.I do not recommend autoremove with apt-getWhile I disagree with this (I find autoremove to be an excellent tool), occasionally problems can occur if one fails to review the packages that autoremove proposes to remove for sanity.  If you choose not to use autoremove, the correct command is:```
sudo apt-get remove postfix --purge
```

---

### Post by slacker9876 on 2009-01-16
> **HotShotDJ said:**
> The correct command to accomplish this is```
sudo apt-get autoremove postfix --purge
```I hope that helps!

EDIT:  Some software has user-specific configuration files that are written to the user's account -- for example .package_name (it could be just a file, or it could be a folder that contains the configuration files).  I don't think postfix has user-specific files, but if it does, you'll want to manually remove those.

That did the job! Thank you!!!!!

---

### Post by HotShotDJ on 2009-01-16
> **slacker9876 said:**
> That did the job! Thank you!!!!!I'm pleased that I could help.  For future reference, you can get the same result using Synaptic Package Manager by right clicking on the package you wish to remove and selecting "Mark for Complete Removal."  Some people prefer the command line, others desire a nice graphical user interface.  Ubuntu gives you both options. :)

---

