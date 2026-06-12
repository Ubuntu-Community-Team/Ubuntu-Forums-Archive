---
title: "Open Office Reinstallation/Upgrade Difficulties"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by osquid on 2009-01-10
Ok, I am just a casual Ubuntu user who has been dual booting between Windows XP and Hardy.

I wanted to upgrade to Open Office 3.0 from 2.0. I uninstalled 2.0 from the 'Add/Remove programs' utility in the Applications menu. 

Mistake #1: I realized after a few google searches that I should have just added the 3.0 repository to the installation utility.

I then attempted to reinstall Open Office by rechecking it in the 'Add/Remove programs' utility in the Applications menu. No dice. I get an error message that says: 

"This application conflicts with other installed software. To install 'openoffice.org' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

I go to the package manager and uninstall all open office related entries and try to reinstall again. I get the same error message. I search the problem on google and use several terminal commands to fix the problem.
apt-get purge, delete, and update say they work after running, but they don't. I continue to get the error message.

What's the problem, and how can I fix it? (short of reinstalling, which I am tempted to try after working on this for over 12 hours.)
:confused:

Thanks in advance.

---

### Post by JoshuaRL on 2009-01-10
When you go to Synaptic and check those packages for complete removal, does it do it?  Are those packages marked as being not installed?

---

### Post by osquid on 2009-01-10
> **JoshuaRL said:**
> When you go to Synaptic and check those packages for complete removal, does it do it?  Are those packages marked as being not installed?

Yes, the packages are marked as uninstalled in the manager.

---

### Post by JoshuaRL on 2009-01-10
Okay.  So what is the error if you mark them for installation and Apply.

---

### Post by osquid on 2009-01-10
openoffice.org-core:
 Depends: libdb4.7  but it is not installable
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
 Depends: libhunspell-1.2-0 (>=1.2.4) but it is not installable
 Depends: libhyphen0 but it is not going to be installed
  Depends: libneon27 (>=0.28.2) but 0.27.2-1 is to be installed

---

### Post by JoshuaRL on 2009-01-10
Alright, lets see if the deb works right.  [Here is the torrent page,](http://distribution.openoffice.org/p2p/) and [here is the download page.](http://download.openoffice.org/other.html#en-US)  Get the deb for the right language and version, and see if that works.

---

