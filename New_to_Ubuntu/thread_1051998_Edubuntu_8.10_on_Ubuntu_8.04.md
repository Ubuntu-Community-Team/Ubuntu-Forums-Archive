---
title: "Edubuntu 8.10 on Ubuntu 8.04"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by japhyr on 2009-01-27
Hello everyone,

I would like to try edubuntu on an old desktop.  I understand that edubuntu is now an add-on on top of a regular ubuntu version.  I want to use ubuntu 8.04 as the base version, because that is what I am using on my laptop.  Is it okay to use edubuntu 8.10 on ubuntu 8.04, or do the versions need to be identical?

---

### Post by Tim Sharitt on 2009-01-27
If you install the edubuntu-desktop package in Ubuntu 8.04, you will have Edubuntu 8.04 installed. To get Edubuntu 8.10 you will need to run a dist-upgrade.

To install edubuntu-desktop (which will install all of the packages included in the Edubuntu desktop system) in install edubuntu-desktop through Synaptic or open a terminal and run:
```
sudo apt-get install edubuntu-desktop
```

To upgrade to 8.10 run:
```
sudo apt-get dist-upgrade
```

---

### Post by japhyr on 2009-01-27
I'm not sure I will have internet access immediately on this computer, so I'm trying to determine which version of edubuntu to download.  I would like to stay with ubuntu 8.04, the LTS release.

Can I use a cd of edubuntu 8.10 to install edubuntu over ubuntu 8.04, or would I need to upgrade ubuntu to 8.10 before I can use edubuntu 8.10?  If edubuntu 8.10 is only compatible with ubuntu 8.10, then I'll go back and download edubuntu 8.04 instead of 8.10.

---

### Post by Tim Sharitt on 2009-01-27
I can't say for sure, but I would assume that you would need the 8.04 version of the eduducation cd for ubuntu 8.04. 8.10 most likely would have dependency issues. 
You can get the Ubuntu 8.10 Alternate install CD and use it to upgrade Ubuntu 8.04 if you don't have internet access.

---

