---
title: "WifiScanner-1.0.0"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Salvage hacker on 2009-05-21
Ok here we go I am trying to install the software and I followed the directions in the readme file. But I get some errors can some please help me install this application. I really would like to use it,

---

### Post by uupreti on 2009-05-21
What is the error you got? can you post it here??

---

### Post by Salvage hacker on 2009-05-21
root@scrspdjohnta:/home/johnta/Desktop/WifiScanner-1.0.0# ./autogen.sh
Prototype mismatch: sub Automake::SEEK_SET: none vs () at /usr/share/perl/5.10/Exporter.pm line 66.
 at /usr/local/bin/automake line 8317
Prototype mismatch: sub Automake::SEEK_CUR: none vs () at /usr/share/perl/5.10/Exporter.pm line 66.
 at /usr/local/bin/automake line 8317
Prototype mismatch: sub Automake::SEEK_END: none vs () at /usr/share/perl/5.10/Exporter.pm line 66.
 at /usr/local/bin/automake line 8317
processing .
aclocal
aclocal: configure.in: 12: macro `AM_ENABLE_STATIC' not found in library
aclocal: configure.in: 347: macro `AM_PATH_GLIB_2_0' not found in library
root@scrspdjohnta:/home/johnta/Desktop/WifiScanner-1.0.0# /etc/alternatives/automake
configure.in:10: version mismatch.  This is Automake 1.10.1,
configure.in:10: but the definition used by this AM_INIT_AUTOMAKE
configure.in:10: comes from Automake 1.9.6.  You should recreate
configure.in:10: aclocal.m4 with aclocal and run automake again.
root@scrspdjohnta:/home/johnta/Desktop/WifiScanner-1.0.0# /etc/alternatives/aclocal
configure.in:331: warning: macro `AM_PATH_GLIB_2_0' not found in library
root@scrspdjohnta:/home/johnta/Desktop/WifiScanner-1.0.0# make
make: *** No targets specified and no makefile found.  Stop.
root@scrspdjohnta:/home/johnta/Desktop/WifiScanner-1.0.0# ./autogen.sh
Prototype mismatch: sub Automake::SEEK_SET: none vs () at /usr/share/perl/5.10/Exporter.pm line 66.
 at /usr/local/bin/automake line 8317
Prototype mismatch: sub Automake::SEEK_CUR: none vs () at /usr/share/perl/5.10/Exporter.pm line 66.
 at /usr/local/bin/automake line 8317
Prototype mismatch: sub Automake::SEEK_END: none vs () at /usr/share/perl/5.10/Exporter.pm line 66.
 at /usr/local/bin/automake line 8317
processing .
aclocal
aclocal: configure.in: 12: macro `AM_ENABLE_STATIC' not found in library
aclocal: configure.in: 347: macro `AM_PATH_GLIB_2_0' not found in library

---

### Post by Salvage hacker on 2009-05-21
this is what I am getting I am trying to install the software and I am just having such a hard time I followed the install instructions

---

