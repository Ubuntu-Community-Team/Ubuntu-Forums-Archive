---
title: "Synaptic/dpkg/deslect/apt-get crashes after trying to install 'splashy'"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by techningeer on 2011-02-14
I am using Ubuntu 10.04LTS 64bit. I installed the package 'splashy' I think and then Software Center told me that the installation failed. I currently have startupmanager installed. Using the command line doesn't work either (apt-get update or aptitude update). It tells me that there is a segmentation fault core dumped. But, Apport crashes when I try to report the problem. Any idea what is going on here? Help is appreciated.
--techningeer

---

### Post by shunan on 2011-02-14
try this

sudo dpkg --configure -a

---

### Post by techningeer on 2011-02-14
I still receive the same error message after I try that.

---

### Post by shunan on 2011-02-14
need more data, maybe apt-get cache got corrupted...

try this and see...

sudo rm -f /var/cache/apt/*.bin
sudo apt-get update

---

### Post by techningeer on 2011-02-14
That solved the apt-get problem. But now when I try to install the package 'splashy-themes' I receive this error message:

E: /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_amd64.deb: trying to overwrite '/etc/lsb-base-logging.sh', which is also in package lsb-base 0

---

### Post by techningeer on 2011-02-14
(Reading database ... 210688 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-5ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/etc/lsb-base-logging.sh', which is also in package lsb-base 0:4.0-0ubuntu8
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of splashy-themes:
 splashy-themes depends on splashy (>= 0.3.12-1); however:
  Package splashy is not installed.
dpkg: error processing splashy-themes (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy-themes

---

### Post by shunan on 2011-02-14
Sorry to report that this is a bug!
[https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089](https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089)

you can try to force install by issuing
sudo dpkg --force-overwrite --install /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_amd64.deb

but do it at your own risk!!!!

---

### Post by techningeer on 2011-02-14
Thanks for your help shunan. I removed those packages. Do you know of any other packages that can change the splash screen?
--techningeeer

---

### Post by shunan on 2011-02-14
havent used one for long time now, you can try

[http://www.webupd8.org/2010/10/install-and-change-plymouth-themes-in.html](http://www.webupd8.org/2010/10/install-and-change-plymouth-themes-in.html)

or 

[http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/](http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/)

also you might be interested in

Start-up-manager
sudo apt-get install startupmanager

always make backups!!! ;)

---

