---
title: "dhcp3-server won't install"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by loop on 2007-08-21
Trying to install dhcp3-server on my router at home but the package seems to be broken.
```

 apt-get install dhcp3-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  dhcp3-server
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 0B/302kB of archives.
After unpacking 856kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/dhcp3-server_3.0.4-12ubuntu4_i386.deb (--unpack):
 files list file for package `libexif12' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/dhcp3-server_3.0.4-12ubuntu4_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Router is an ordinary PC with Feisty installed on it. I've tried updating from the repositories but that didn't seem to help.

---

### Post by nitro_n2o on 2007-08-21
sudo apt-get autoclean
sudo apt-get update 
then install your package

---

### Post by loop on 2007-08-21
Thank you for the suggestion but it still gives the same after when trying to install after I've performed your commands.

---

