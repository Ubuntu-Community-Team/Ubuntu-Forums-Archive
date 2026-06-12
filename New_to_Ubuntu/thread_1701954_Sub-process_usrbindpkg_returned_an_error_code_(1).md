---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by euloiix on 2011-03-07
Hi everyone,

Here is what is bothering me. I try to be able to read mp3 and to have my youtube working properly (which is not yet!). Anyway, I am trying to solve it installing the following packages: 
[B]- sudo apt-get install ubuntu-restricted-extras
- sudo apt-get install ubuntu-restricted-addons[/B]

Here is what I obtain: 

[HTML]euloiix@euloiix-Aspire-8530:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ttf-mscorefonts-installer unrar
The following NEW packages will be installed:
  ttf-mscorefonts-installer ubuntu-restricted-extras unrar
0 upgraded, 3 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B/149kB of archives.
After this operation, 516kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package ttf-mscorefonts-installer.
(Reading database ... 120575 files and directories currently installed.)
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.2ubuntu2_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/ttf-mscorefonts-installer_3.2ubuntu2_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package ubuntu-restricted-extras.
Unpacking ubuntu-restricted-extras (from .../ubuntu-restricted-extras_42_i386.deb) ...
Selecting previously deselected package unrar.
Unpacking unrar (from .../unrar_1%3a3.9.10-1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/ttf-mscorefonts-installer_3.2ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


&&


euloiix@euloiix-Aspire-8530:~$ sudo apt-get install ubuntu-restricted-addons
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-addons is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up man-db (2.5.7-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ubuntu-restricted-extras (42) ...
Setting up unrar (1:3.9.10-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode.
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]


Do not hesitate if you have any idea what the problem might be.
Thanks in advance.
:D

---

### Post by TeoBigusGeekus on 2011-03-07
From the following:
[LIST]
[*]software-centre
[*]synaptic
[*]apt-get
[/LIST]
you can have only one running.
If you want to run apt-get, close software centre and/or synaptic.

---

### Post by euloiix on 2011-03-07
Thanks !

---

