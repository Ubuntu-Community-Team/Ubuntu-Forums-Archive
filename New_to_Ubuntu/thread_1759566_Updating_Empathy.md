---
title: "Updating Empathy"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by avelez89 on 2011-05-15
Hello everyone, first I'd like to thank you for taking some time to try and help me!

I need mobile contact icon indicators in Empathy, and found this bug report which basically says that it's been fixed but the fix didn't make it into Natty. I was wondering, how can I get it working?

I tried adding the PPA and upgrading (requires dist-upgrade)

```
andres@andres-ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  empathy nautilus-sendto-empathy
The following NEW packages will be installed:
  libcanberra-gtk3-0 libcanberra-gtk3-module libclutter-gtk-1.0-0 libgail-3-0
  libgtk-3-0 libgtk-3-bin libgtk-3-common libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common
The following packages will be upgraded:
  empathy-common
1 upgraded, 9 newly installed, 2 to remove and 0 not upgraded.
Need to get 0 B/12.8 MB of archives.
After this operation, 38.5 MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

If I do accept, Empathy is removed and can't be installed anymore. I'm not sure what to do.

Thank you for your help!

---

