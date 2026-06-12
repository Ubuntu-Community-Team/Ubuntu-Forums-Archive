---
title: "Firefox upgrade corruption now lost browser"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by hughcrowther on 2010-01-09
I enabled the upgrade posted this morning but then lost firefox - could not uninstall the remaining bits could not fully install what was there - after sudo apt-get install firefox - got most reinstalled untill we get to this lie and as you see it seems to have messed up ;
Setting up xulrunner-1.9.1 (1.9.1.7+nobinonly-0ubuntu0.9.10.1) ...
Bus error
dpkg: error processing xulrunner-1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-gnome-support:
 xulrunner-1.9.1-gnome-support depends on xulrunner-1.9.1 (= 1.9.1.7+nobinonly-0ubuntu0.9.10.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on xulrunner-1.9.1 (>= 1.9.1); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5-branding:
 firefox-3.5-branding depends on firefox-3.5 (= 3.5.7+nobinonly-0ubuntu0.9.10.1); however:
  Package firefox-3.5 is not configured yet.
dpkg: error processing firefox-3.5-brandNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      ing (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.5; however:
  Package firefox-3.5 is not configured yet.
 firefox depends on firefox-3.5-branding; however:
  Package firefox-3.5-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not installed.
  Package firefox-3.5 which provides firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9.1
 xulrunner-1.9.1-gnome-support
 firefox-3.5
 firefox-3.5-branding
 firefox
 ubufox
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas anyone?

---

### Post by hughcrowther on 2010-01-09
Iv'e just tried to install another browser but it's not installing as it refers to the above problem I think the XLrunner bit so now ubuntu software center is defunct.

---

### Post by hughcrowther on 2010-01-09
all ok just reinstalled all xul stuff in syn pac manger: now working again!

---

