---
title: "python wont upgrade and keeps me from installing anything. help"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by AnthKillAllen on 2010-08-18
E: /var/cache/apt/archives/libpython2.6_2.6.5-1ubuntu6_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libpython2.6.so.1.0')

---

### Post by ercferret18 on 2010-08-18
try "sudo apt-get -f install" (in a terminal)

---

### Post by AnthKillAllen on 2010-08-18
anthony@anthony-laptop:~$ sudo apt-get -f install
[sudo] password for anthony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  fglrx-kernel-source
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpython2.6
The following packages will be upgraded:
  libpython2.6
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/986kB of archives.
After this operation, 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 167406 files and directories currently installed.)
Preparing to replace libpython2.6 2.6.4~rc2-0ubuntu1 (using .../libpython2.6_2.6.5-1ubuntu6_i386.deb) ...
Unpacking replacement libpython2.6 ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/libpython2.6_2.6.5-1ubuntu6_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/libpython2.6.so.1.0')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Errors were encountered while processing:
 /var/cache/apt/archives/libpython2.6_2.6.5-1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
anthony@anthony-laptop:~$ 




that happened now

---

### Post by AnthKillAllen on 2010-08-19
please help it happened after upgrade to new ubuntu version

---

