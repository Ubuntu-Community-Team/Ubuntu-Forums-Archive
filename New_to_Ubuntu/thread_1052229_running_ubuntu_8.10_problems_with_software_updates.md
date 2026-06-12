---
title: "running ubuntu 8.10 problems with software updates and adding prgrams"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by michaeledward on 2009-01-27
now i am having problems trying to get amarok to install.. when i select it through the add apps it keeps saying error. i figured out that i need to have libvisual-0.4 plugin but when i try to install the updates it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

then i try to manually run the command in the terminal and it says requested operation requires superuser priv.


any help?!?!

p.s. its great that people out there are actually willing to help guys like me. this website is great.

mike

---

### Post by taurus on 2009-01-27
Just add the sudo in front of the command for root privilege.  Use the same password that you are logged in with.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by michaeledward on 2009-01-27
when i run that command after everything runs this is what it says at the end.



Setting up avahi-utils (0.6.23-2ubuntu2.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
Errors were encountered while processing:
 compiz-fusion-plugins-main

---

### Post by michaeledward on 2009-01-27
this also came up when i tried to run the sudo command again.


dpkg: error processing compiz-fusion-plugins-main (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 compiz-fusion-plugins-main


i went in to the package manager and it wont let me reinstall from there...sorry guys im really really new to ubuntu

---

