---
title: "[SOLVED] Error: Broken Count&amp;gt;0"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by cjv8888 on 2009-01-02
I did a fresh install of Hardy and after a whole lot of updates I was left with the above error.
After some research on the forum, I did 
sudo apt-get update  and
sudo apt-get upgrade

then did a

sudo apt-get -f install

but still ended up with the errors below:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  evolution-common linux-restricted-modules-2.6.24-22-generic
Suggested packages:
  avm-fritz-firmware-2.6.24-22
The following NEW packages will be installed:
  linux-restricted-modules-2.6.24-22-generic
The following packages will be upgraded:
  evolution-common
1 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
5 not fully installed or removed.
Need to get 0B/34.3MB of archives.
After this operation, 48.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 113670 files and directories currently installed.)
Preparing to replace evolution-common 2.22.1-0ubuntu3 (using .../evolution-common_2.22.3.1-0ubuntu1_all.deb) ...
Unpacking replacement evolution-common ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/evolution-common_2.22.3.1-0ubuntu1_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/evolution/2.22/images/world_map-960.png')
Unpacking linux-restricted-modules-2.6.24-22-generic (from .../linux-restricted-modules-2.6.24-22-generic_2.6.24.14-22.53_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-restricted-modules-2.6.24-22-generic_2.6.24.14-22.53_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./lib/linux-restricted-modules/2.6.24-22-generic/nvidia/os-agp.o')
Errors were encountered while processing:
 /var/cache/apt/archives/evolution-common_2.22.3.1-0ubuntu1_all.deb
 /var/cache/apt/archives/linux-restricted-modules-2.6.24-22-generic_2.6.24.14-22.53_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What else should I do?
Thanks in advance.

---

### Post by cjv8888 on 2009-01-02
If there is no way to install those packages, how do I get rid of the notification or elect not to install them?

---

### Post by handydan918 on 2009-01-02
Sometimes aptitude can solve dependency issues apt can't. 
Try ```
aptitude install packagename
``` where packagename is the name of one of the packages listed in the output of your error mesaage. 
In the alternative, you might try the same command but remove instead of install. Aptitude will offer possible solutions. Read them carefully. 
Good luck.

---

### Post by nemilar on 2009-01-02
perhaps try

```
sudo apt-get clean ; sudo apt-get autoclean
```

then

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cjv8888 on 2009-01-02
Thanks.

Running aptitude did not work but after running clean and auto clean

and re-running

sudo apt-get -f install

the packages are installed. :D

---

