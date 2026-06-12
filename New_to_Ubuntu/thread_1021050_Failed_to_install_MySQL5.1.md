---
title: "Failed to install MySQL5.1"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by poiu999 on 2008-12-24
Hi, I tried to install MySQL5.1 on ubuntu8.10 but failed. The console displayed below message:

=========================================
...
...
Selecting previously deselected package mysql-client-5.1.
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.22rc-2~ppa5_i386.deb) ...
Selecting previously deselected package mysql-server-5.1.
dpkg: regarding .../mysql-server-5.1_5.1.22rc-2~ppa5_i386.deb containing mysql-server-5.1, pre-dependency problem:
 mysql-server-5.1 pre-depends on mysql-common (>= 5.1.22rc-2~ppa5)
  mysql-common is unpacked, but has never been configured.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.22rc-2~ppa5_i386.deb (--unpack):
 pre-dependency problem - not installing mysql-server-5.1
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.1_5.1.22rc-2~ppa5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
========================================================

As part of the MySQL package has been installed (as there are many messages state unpacking...), I would like to know how to remove them. 

Thanks in advance for any help.

---

### Post by namdung on 2008-12-24
I reckon u have a broken package. Try fixing it first

sudo dpkg --configure -a

or find broken packages in Synaptic Package Manager. Use Synaptic for hassle free installation of MySQL

---

### Post by poiu999 on 2008-12-25
> **namdung said:**
> I reckon u have a broken package. Try fixing it first

sudo dpkg --configure -a

or find broken packages in Synaptic Package Manager. Use Synaptic for hassle free installation of MySQL

Thanks for your help. It seems the current "best" version is MySQL5.0 based on Synaptic. Don't know how long it will change to 5.1.
Thanks

---

