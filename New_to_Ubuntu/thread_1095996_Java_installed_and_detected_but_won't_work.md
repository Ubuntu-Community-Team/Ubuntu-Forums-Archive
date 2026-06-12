---
title: "Java installed and detected but won't work"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by abooks on 2009-03-14
I've been trying to download java to my ubuntu and kubuntu machines and it just won't work. This morning I used the pkg mgr to download the sun version (since the open one didn't work) and selected it as default. when that didn't work I deleted the original open ware version, but it STILL doesn't work and isn't detected by sun.

Any other ideas?

---

### Post by taurus on 2009-03-14
Have you tried to install the version in the repos?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by abooks on 2009-03-14
Did that and it still doesn't work. Here's what it said:

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
abooks@humboldt1:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
The following packages were automatically installed and are no longer required:
  libggzmod4 libggz2 libggzcore9
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  sun-java6-plugin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1966B of archives.
After this operation, 102kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse sun-java6-plugin 6-07-3ubuntu2 [1966B]
Fetched 1966B in 0s (2143B/s)                          
Selecting previously deselected package sun-java6-plugin.
(Reading database ... 142387 files and directories currently installed.)
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-07-3ubuntu2_i386.deb) ...
Setting up sun-java6-plugin (6-07-3ubuntu2) ...

---

### Post by taurus on 2009-03-14
Did you restart firefox?  Sometimes, rebooting would fix it too.

---

### Post by abooks on 2009-03-14
Mo bettah now! Mahalo!

---

