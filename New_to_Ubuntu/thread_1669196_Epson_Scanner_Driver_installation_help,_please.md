---
title: "Epson Scanner Driver installation help, please"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by mikeprosceo on 2011-01-17
I am trying to load the linux driver for an epson 3170 scanner on to my ubuntu 10.10 64 bit laptop. I downloaded the rpm package (iscan-2.10.0-1.c2.i386.rpm and iscan-plugin-gt-9400-1.10.0-1.c2.i386.rpm) to my desktop. I extracted the files and and tried to use alien to convert the rpm to a deb file in terminal. The following are the steps I took and the message I received. Before I tried this I installed libsane-dev. and libsane-extras.
michael@michael-laptop:~/Desktop$ sudo alien -d iscan-2.10.0-1.c2.i386.rpm
Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `iscan-2.10.0': File exists
unable to mkdir iscan-2.10.0: at /usr/share/perl5/Alien/Package.pm line 257.
I also tried using sudo alien -k iscan.2.10.0-1.c2.i386.rpm and got a file not found message. I am totally lost and have no idea what to try. Can anyone help? Thanks - Mike

---

### Post by Mark Phelps on 2011-01-17
Sorry ... but converting rpm to deb is a very hit-and-miss proposition.  Some packages convert well; others do not.

Main problem I ran into when doing this in the past is that some of the libraries, and their members, are named differently in the rpm packages than they are in the deb packages -- which meant tracking down the individual library packages (usually of the "dev" variety) that had to be then installed.

---

