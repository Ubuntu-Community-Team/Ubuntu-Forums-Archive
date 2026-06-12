---
title: "Ddownload  and installOpen Office 3"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Roger Gundberg on 2009-02-03
This link worked for me:
#!/bin/sh

wget [ftp://ftp.tu-chemnitz.de/pub/openoffice-extended/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz](ftp://ftp.tu-chemnitz.de/pub/openoffice-extended/stable/3.0.0/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz)

tar -xvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

cd OOO300_m9_native_packed-1_en-US.9358

cd DEBS

sudo dpkg -i *.deb

cd desktop-integration

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

---

### Post by icheyne on 2009-02-04
Installing via the repositories makes upgrades easier - [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml).

---

