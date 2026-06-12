---
title: "Trouble reinstalling openoffice"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by aburgess on 2011-02-10
I replaced openoffice with libreoffice, but now I want to go back and apt-get isn't working:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 openoffice.org : Depends: openoffice.org-core (= 1:3.2.1-7ubuntu1.1) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
                  Depends: openoffice.org-filter-mobiledev but it is not going to be installed
                  Depends: openoffice.org-java-common (>= 1:3.2.1~) but it is not going to be installed
                  Recommends: openoffice.org-filter-binfilter but it is not going to be installed
E: Broken packages

```Ubuntu Software Centre says:

Package dependencies cannot be resolved. This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

I uninstalled libreoffice in a pretty sketchy way, i.e. selected a few things in the software centre that said "libreoffice" and told it to uninstall them.

How can I get openoffice back?

---

### Post by Hagar Delest on 2011-02-10
Try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

But you have to make sure there is no broken packages left first.

---

### Post by aburgess on 2011-02-10
Merci, ca marche bien!

---

