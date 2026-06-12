---
title: "Problems installing Samba on a fresh Ubuntu 18.04 LTS install"
date: 2019-09-26
forum: Networking &amp; Wireless
---

### Post by roguegeek on 2019-09-26
Set up a new server. I installed a fresh Ubuntu 18.04.3 LTS, ran a  standard software update, and installed a video driver. That is all I've  done. Now I'm simply trying to install Samba onto the system.


  So I do:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install samba
```
Updates and upgrades runs fine. It's on the install that I get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  samba-libs

E: Package 'samba' has no installation candidate
```
I feel like I've installed Samba a decent amount of times and have never  seen this error. Can someone explain what is going on and how to  address it?

---

