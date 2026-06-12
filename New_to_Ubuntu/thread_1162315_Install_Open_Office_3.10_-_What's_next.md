---
title: "Install Open Office 3.10 - What's next?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by bsmith52 on 2009-05-17
I wanted to install Open Office 3.10 because it seemed to be the easiest way to extract text from a .pdf file (in conjunction with pdfimport.oxt).  I uninstalled all the native version (I had Open Office 2.4 on ubuntu 8.10) via the Synaptice Package manager. From there:

bill@bill-desktop:~/Desktop$ ls
basic                                          pdfimport.oxt
description.xml                                pdfimport.uno.so
help                                           pdf_types.xcu
META-INF                                       registration
OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz  xpdfimport
pdf_import_filter.xcu                          xpdfimport_err.pdf
bill@bill-desktop:~/Desktop$ sudo tar xfvz OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz
[sudo] password for bill: 
OOO310_m11_native_packed-4_en-US.9399/
OOO310_m11_native_packed-4_en-US.9399/DEBS/

....

OOO310_m11_native_packed-4_en-US.9399/licenses/LICENSE_en-US
OOO310_m11_native_packed-4_en-US.9399/licenses/LICENSE_en-US.html
OOO310_m11_native_packed-4_en-US.9399/update
bill@bill-desktop:~/Desktop$ ls
basic                                          pdfimport.oxt
description.xml                                pdfimport.uno.so
help                                           pdf_types.xcu
META-INF                                       registration
OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz  xpdfimport
OOO310_m11_native_packed-4_en-US.9399          xpdfimport_err.pdf
pdf_import_filter.xcu

(THIS IS ME ATTEMPTING TO DO THE dpkg COMMAND FOR THE ENTIRE DIRECTORY)

bill@bill-desktop:~/Desktop$ cd OOO310_m11_native_packed-4_en-US.9399
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399$ ls
DEBS  licenses  readmes  update
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399$ DEBS
bash: DEBS: command not found
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399$ dpkg --install DEBS
dpkg: requested operation requires superuser privilege
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399$ sudo dpkg --install DEBS
dpkg-split: error reading DEBS: Is a directory
dpkg: error processing DEBS (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 DEBS
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399$ sudo dpkg -i DEBS
dpkg-split: error reading DEBS: Is a directory
dpkg: error processing DEBS (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 DEBS
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399$ ls
DEBS  licenses  readmes  update
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399$ cd DEBS
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS$ LS
The program 'LS' is currently not installed.  You can install it by typing:
sudo apt-get install sl
bash: LS: command not found
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS$ ls
desktop-integration
ooobasis3.1-base_3.1.0-11_i386.deb
ooobasis3.1-binfilter_3.1.0-11_i386.deb
......
openoffice.org3-writer_3.1.0-11_i386.deb
openoffice.org-ure_1.5.0-11_i386.deb
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS$ sudo -i *.deb
-bash: ooobasis3.1-base_3.1.0-11_i386.deb: No such file or directory

(FINALLY FIGURED IT OUT)

bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS$ sudo dpkg --install *.deb
Selecting previously deselected package ooobasis3.1-base.
(Reading database ... 135338 files and directories currently installed.)
Unpacking ooobasis3.1-base (from ooobasis3.1-base_3.1.0-11_i386.deb) ...
Selecting previously deselected package ooobasis3.1-binfilter.
.....
Selecting previously deselected package openoffice.org3-writer.
Unpacking openoffice.org3-writer (from openoffice.org3-writer_3.1.0-11_i386.deb) ...
Selecting previously deselected package openoffice.org-ure.
Unpacking openoffice.org-ure (from openoffice.org-ure_1.5.0-11_i386.deb) ...
Setting up openoffice.org-ure (1.5.0-11) ...
Setting up ooobasis3.1-core01 (3.1.0-11) ...
Setting up ooobasis3.1-core02 (3.1.0-11) ...

.....
Setting up ooobasis3.1-binfilter (3.1.0-11) ...
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS$ 

What is next to get my Open Office 3.10 to work?

Thanx, Bill

---

### Post by gjoellee on 2009-05-17
Check this website: [http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by bsmith52 on 2009-05-17
Looks like I had it right, til the last part: Getting the lauch icon into the Applications window.  The tutorial worked great! Thanks a mucho, Bill

---

