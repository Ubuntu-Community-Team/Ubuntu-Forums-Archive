---
title: "how to install libgdbm3 with Ubuntu 11.04"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by mandevip on 2011-08-04
I am using Ubuntu 11.04 on a 386 computer.

I am following the code and examples in Brian Gough's 2005 An Introduction to GCC. On page 20 the code utilizes the GNU Database Management Library (GDBM).

I tried to install libgdbm3 with both Synaptic Package Manager and with the following code:
 
peter@peter-BNB:~$ sudo apt-get install libgdbm3
[sudo] password for peter: 

with the following results:
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgdbm3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I then tried unsuccesfully to find the location of the files:

peter@peter-BNB:~$ locate libgdbm3
/usr/share/doc/libgdbm3
/usr/share/doc/libgdbm3/changelog.Debian.gz
/usr/share/doc/libgdbm3/copyright
/var/cache/apt/archives/libgdbm3_1.8.3-9ubuntu1_i386.deb
/var/lib/dpkg/info/libgdbm3:i386.list
/var/lib/dpkg/info/libgdbm3:i386.md5sums
/var/lib/dpkg/info/libgdbm3:i386.postinst
/var/lib/dpkg/info/libgdbm3:i386.postrm
/var/lib/dpkg/info/libgdbm3:i386.shlibs
/var/lib/dpkg/info/libgdbm3:i386.symbols

What to I have to do to install the package correctly?

Thank you very much.

mandevip

---

### Post by cogier on 2011-08-04
If you run Synaptic Package Manager and put "libgdbm" in the search box and press [Enter]. Right click on the item(s) the search returns and select "Properties". The result I got using 10.10 is below.

/.
/usr
/usr/lib
/usr/lib/libgdbm.so.3
/usr/lib/libgdbm.so.3.0.0
/usr/lib/libgdbm_compat.so.3
/usr/lib/libgdbm_compat.so.3.0.0
/usr/share
/usr/share/doc
/usr/share/doc/libgdbm3
/usr/share/doc/libgdbm3/changelog.Debian.gz
/usr/share/doc/libgdbm3/changelog.gz
/usr/share/doc/libgdbm3/copyright
/usr/share/info
/usr/share/info/gdbm.info.gz
/usr/share/man
/usr/share/man/man3
/usr/share/man/man3/gdbm.3.gz

---

