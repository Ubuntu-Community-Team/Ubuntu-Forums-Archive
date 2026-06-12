---
title: "Can't uninstall program - error exit status 2"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by Ezrie on 2010-07-28
Hi.  I am trying to unistall x2go, specifically the x2gognomebindings package.  See screenshot for synaptic error and see below for the reults of sudo apt-get -f install

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up x2gognomebindings (2.0.1-1) ...
Settings menu not found in /etc/xdg/menus at /usr/sbin/update-gnome-menu-x2go line 22.
dpkg: error processing x2gognomebindings (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 x2gognomebindings
E: Sub-process /usr/bin/dpkg returned an error code (1)
ezrie@K-Laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up x2gognomebindings (2.0.1-1) ...
Settings menu not found in /etc/xdg/menus at /usr/sbin/update-gnome-menu-x2go line 22.
dpkg: error processing x2gognomebindings (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 x2gognomebindings
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks

---

### Post by Elmer Fudd on 2010-07-28
Have you tried booting into recovery mode and using:
sudo apt-get remove <package name>
from the command line?

---

### Post by iponeverything on 2010-07-28
find the x2gognomebindings deb /var/cache/apt/archives.

Use dpkg to list the contents of the package and then identify files that it places in /etc/xdg/menus.

Create empty files with those name/s in /etc/xdg/menus as place holders. 

rerun the package removal.

---

### Post by Ezrie on 2010-09-04
> **iponeverything said:**
> find the x2gognomebindings deb /var/cache/apt/archives.

Use dpkg to list the contents of the package and then identify files that it places in /etc/xdg/menus.

Create empty files with those name/s in /etc/xdg/menus as place holders. 

rerun the package removal.

Sounds like a plan.  Can someone please please walk me through how to do this?

---

