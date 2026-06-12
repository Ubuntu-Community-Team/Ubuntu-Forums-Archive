---
title: "install webmin"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by mustafa ibrahim on 2011-05-05
when i am trying to install webmin i downloaded the source and i trying to install i found 
Current status: 0 broken [-1], 106 updates [-3], 31218 new [-1].
root@mustafa-sr1:/home/mustafa-sr1# ls
core              webmin-1.310         webmin_1.441_all.deb
webmin_1.290.deb  webmin-1.310.tar.gz  webmin-current.deb
root@mustafa-sr1:/home/mustafa-sr1# dpkg -i webmin_1.441_all.deb
Selecting previously deselected package webmin.
(Reading database ... 45642 files and directories currently installed.)
Unpacking webmin (from webmin_1.441_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin
root@mustafa-sr1:/home/mustafa-sr1# apt-get --install
E: Command line option --install is not understood

---

### Post by sandyd on 2011-05-05
> **mustafa ibrahim said:**
> when i am trying to install webmin i downloaded the source and i trying to install i found 
Current status: 0 broken [-1], 106 updates [-3], 31218 new [-1].
root@mustafa-sr1:/home/mustafa-sr1# ls
core              webmin-1.310         webmin_1.441_all.deb
webmin_1.290.deb  webmin-1.310.tar.gz  webmin-current.deb
root@mustafa-sr1:/home/mustafa-sr1# dpkg -i webmin_1.441_all.deb
Selecting previously deselected package webmin.
(Reading database ... 45642 files and directories currently installed.)
Unpacking webmin (from webmin_1.441_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin
root@mustafa-sr1:/home/mustafa-sr1# apt-get --install
E: Command line option --install is not understood
```

sudo apt-get -f install
```
will sort webmin out.

---

### Post by gg234 on 2011-05-06
try this [http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-11-04-natty-server.html](http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-11-04-natty-server.html)

---

