---
title: "Openoffice install error"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by AlexCSU on 2011-03-05
I'm pretty new to Ubuntu and am currently running version 10.4

Openoffice has not been opening. When clicked on in the applications menu, the computer slows down, the openoffice screen show up, and then goes away. I removed openoffice with "apt-get remove" and while reinstalling had the following error.

E: openoffice.org-filter-binfilter: subprocess installed post-installation script returned error exit status 135

the report also listed several "bus error"

Any help/guidence is greatly appreciated! As a student openoffice is kind of important to me. Thank you!

---

### Post by maqtanim on 2011-03-06
Welcome to UF! :)

Can you just run the following command
```
sudo apt-get -f install
```
Then try to reinstall again?

---

### Post by AlexCSU on 2011-03-06
after the apt-get -f install the following was displayed

```
Bus error
dpkg: error processing openoffice.org-filter-binfilter (--configure):
 subprocess installed post-installation script returned error exit status 135
Errors were encountered while processing:
 openoffice.org-filter-binfilter
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

when reinstalling openoffice I recieved 

```
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up openoffice.org-filter-binfilter (1:3.2.0-7ubuntu4.2) ...
Bus error
Bus error
dpkg: error processing openoffice.org-filter-binfilter (--configure):
 subprocess installed post-installation script returned error exit status 135
Errors were encountered while processing:
 openoffice.org-filter-binfilter
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Do you need me to paste more of what the terminal displayed or did I copy enough?

---

