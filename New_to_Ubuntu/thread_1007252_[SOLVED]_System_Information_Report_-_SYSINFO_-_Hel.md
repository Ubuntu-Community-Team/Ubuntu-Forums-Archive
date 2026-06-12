---
title: "[SOLVED] System Information Report - SYSINFO - Help About"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by gmgj on 2008-12-10
I am looking for a program that generates a list of the major components of my system.

Linux Distro and Version
Gnome , KDE or something else 
Some Hardware Information
A list of the major installed packages 

-------------------------------------------

To put it another way, suppose you are a user looking for another editor, and you go to install package and it says this  

The GNU Emacs editor (Emacs 22) 
GNU Emacs is the extensible self-documenting text editor. This package contains a version of Emacs compiled with support for X.
**If you have GTK+ 2.x **installed on your system, you will probably have a better experience with the emacs22-gtk package, instead of this one.

How would I figure out if I have GTK+2.x installed?
How do I know if I have GTK+ 2.x?

---

### Post by iponeverything on 2008-12-10
> Linux Distro and Version


cat /etc/lsb-release |grep DESCRIPTION

> Gnome , KDE or something else

?

> Some Hardware Information
lshw -short

> A list of the major installed packages

dpkg -l

---

### Post by gmgj on 2008-12-10
Thanks, This is what I did

#!/bin/bash 
#WARNING: you should run this program as super-user.
#don't forget to chmod u+rx SomeSysInfo and to run with ./SomeSysinfo
echo ""
echo "$0 in $PWD on `date` by `whoami` Bash Version ${BASH_VERSINFO[*]}" >SomeSysinfo.txt
echo "___ cut -d_ -f2 /etc/lsb-release ___________________________________________" >>SomeSysinfo.txt
cut -d_ -f2 /etc/lsb-release >>SomeSysinfo.txt
echo "___ uname -a _______________________________________________________________" >>SomeSysinfo.txt
uname -a >>SomeSysinfo.txt
echo "___ df -h __________________________________________________________________" >>SomeSysinfo.txt
df -h	>>SomeSysinfo.txt

echo "___ lshw -short ____________________________________________________________" >>SomeSysinfo.txt
lshw -short >>SomeSysinfo.txt
echo "___ dpkg -l ________________________________________________________________" >>SomeSysinfo.txt
dpkg -l >>SomeSysinfo.txt
echo "___ set ___________________________________________________________________" >>SomeSysinfo.txt
set >>SomeSysinfo.txt
echo "___ cat /var/lib/locales/supported.d/local ________________________________" >>SomeSysinfo.txt
cat /var/lib/locales/supported.d/local >>SomeSysinfo.txt
echo "____________________________________________________________________________" >>SomeSysinfo.txt

gedit SomeSysinfo.txt

---

