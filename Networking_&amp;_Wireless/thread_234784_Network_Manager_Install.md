---
title: "Network Manager Install"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by cduffner on 2006-08-12
I have the notoriously troublesome Broadcom BCM4318 Wireless PCI Card on my Gateway desktop computer.  Trying to get it to work, I attempted to install ndiswrapper and Network Manager.  Apparently, ndiswrapper installed correctly and Network Manager had some "dependency problems."  Here is the log file.  (Please help -- Thank you in advance!)

This is the log of the ndiswrapper-setup script. See below for log details.
Log of dpkg -i ndiswrapper.deb 
Sat Aug 12 00:41:58 2006

Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 69523 files and directories currently installed.)
Unpacking ndiswrapper-utils (from ndiswrapper.deb) ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...


Sat Aug 12 00:42:04 2006
----------------
Log of dpkg -i nm-i386.deb 
Sat Aug 12 00:42:07 2006

Selecting previously deselected package network-manager.
(Reading database ... 69536 files and directories currently installed.)
Unpacking network-manager (from nm-i386.deb) ...
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on libnl1-pre6; however:
  Package libnl1-pre6 is not installed.
 network-manager depends on libnm-util0; however:
  Package libnm-util0 is not installed.
 network-manager depends on dhcdbd (>= 1.10-0ubuntu2); however:
  Package dhcdbd is not installed.
dpkg: error processing network-manager (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 network-manager
dpkg died with exit status 1

Sat Aug 12 00:42:07 2006
----------------
This is the log of the ndiswrapper-setup script. See below for log details.
Log of dpkg -i ndiswrapper.deb 
Sat Aug 12 01:29:10 2006

(Reading database ... 69536 files and directories currently installed.)
Preparing to replace ndiswrapper-utils 1.8-0ubuntu2 (using ndiswrapper.deb) ...
Unpacking replacement ndiswrapper-utils ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...


Sat Aug 12 01:29:16 2006
----------------
Log of dpkg -i nm-i386.deb 
Sat Aug 12 01:29:19 2006

Selecting previously deselected package network-manager.
(Reading database ... 69536 files and directories currently installed.)
Unpacking network-manager (from nm-i386.deb) ...
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on libnl1-pre6; however:
  Package libnl1-pre6 is not installed.
 network-manager depends on libnm-util0; however:
  Package libnm-util0 is not installed.
 network-manager depends on dhcdbd (>= 1.10-0ubuntu2); however:
  Package dhcdbd is not installed.
dpkg: error processing network-manager (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 network-manager
dpkg died with exit status 1

Sat Aug 12 01:29:19 2006
----------------

---

### Post by cduffner on 2006-08-12
I should add that I do not have wired internet access on the computer.  I have a dual-boot system with Windows XP Media Center Edition and Dapper Drake.

I can read ext2/ext3 partitions from Windows, so I can put drivers/.tars right onto my desktop through explorer.

---

