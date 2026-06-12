---
title: "Update manager"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by waqas300 on 2011-08-14
Unable to update using update manager it gives error

The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

after doing apt-get install -f

it says


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed:
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 120 not upgraded.
1 not fully installed or removed.
Need to get 0 B/22.1 MB of archives.
After this operation, 68.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 133929 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.840-0ubuntu4_i386.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1):confused:

---

### Post by Rubi1200 on 2011-08-15
Hi,
open a terminal and try the following commands (post error messages like before):

```
sudo apt-get clean
sudo apt-get autoclean
sudo dpkg --configure -a
sudo apt-get update
```

Let us know what happens please.

---

### Post by waqas300 on 2011-08-15
> **Rubi1200 said:**
> Hi,
open a terminal and try the following commands (post error messages like before):

```
sudo apt-get clean
sudo apt-get autoclean
sudo dpkg --configure -a
sudo apt-get update
```

Let us know what happens please.

Seems like update manager is back to normal :P Thanks you so much guys for your kind support.

---

### Post by Rubi1200 on 2011-08-16
Glad you got things sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

