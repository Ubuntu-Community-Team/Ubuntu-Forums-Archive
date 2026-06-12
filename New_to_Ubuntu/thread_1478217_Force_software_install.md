---
title: "Force software install"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by parameter on 2010-05-09
Hi everyone. I want to install Gourmet Recipe Manager but it conflicts with Miro because of python-pysqlite2. How do I force Gourmet Recipe Manager to install without removing Miro or python-pysqlite2 (which Miro needs)?

---

### Post by Nxion on 2010-05-12
Can you post the error your getting? YOu might not have to force anything. It might be asking for a dependency it needs.

---

### Post by mKlRivPwner on 2011-03-18
I'm having the same issue.  It is not an error message.  When attempting to install Miro, it forces an uninstall of Gourmet Recipe Manager and vice-versa through Software Center.  You receive a pop-up[ stating that in order to install one "the following software must be removed" and it lists the other.

---

### Post by dmizer on 2011-03-18
Looks like a bug.

Here is a copy of the error when attempting to install miro:
```
gourmet: Conflicts: python-pysqlite2 (>= 2.5) but 2.6.0-1 is to be installed.
```

If you like, you can open a bug on it:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by parameter on 2011-03-25
The problem seems to be confined to the package in the repositories. I installed the .deb package from the Gourmet Recipe Manager web site and it worked fine with Miro installed.

You can find the release here: [http://sourceforge.net/projects/grecipe-manager/files/0.15.6/gourmet_0.15.6-2_all.deb/download](http://sourceforge.net/projects/grecipe-manager/files/0.15.6/gourmet_0.15.6-2_all.deb/download)

---

