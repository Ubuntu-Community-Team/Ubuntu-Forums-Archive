---
title: "NORMUNDS ihaf no wirles"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by norceks on 2013-12-28
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-lpphy-installer
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 22.7 kB of archives.
After this operation, 119 kB of additional disk space will be used.
Do you want to continue [Y/n]?  
Get:1 [http://lt.archive.ubuntu.com/ubuntu/](http://lt.archive.ubuntu.com/ubuntu/) precise/main b43-fwcutter amd64 1:015-9 [19.3 kB]
Get:2 [http://lt.archive.ubuntu.com/ubuntu/](http://lt.archive.ubuntu.com/ubuntu/) precise/multiverse firmware-b43-lpphy-installer all 1:015-9 [3,390 B]
Fetched 22.7 kB in 0s (58.0 kB/s)                         
Selecting previously unselected package b43-fwcutter.
(Reading database ... 207011 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_amd64.deb) ...
Selecting previously unselected package firmware-b43-lpphy-installer.
Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43-lpphy-installer (1:015-9) ...
No chroot environment found. Starting normal installation
No supported card found.
Use proper b43 or b43legacy firmware.
Aborting.
normunds@normunds-Inspiron-5537:~$

---

### Post by varunendra on 2014-01-01
Welcome to the forums norceks !

Please give us a little description of the problem you are having. From the above outputs, it seems you tried to install a broadcom firmware but it doesn't support your card. So which card do you have? To let us see that, please post the output of -
```
lspci -nnk | grep -iA2 net
```

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

