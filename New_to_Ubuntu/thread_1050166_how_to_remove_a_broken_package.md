---
title: "how to remove a broken package"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by lime4x4 on 2009-01-25
how do i remove the following broken package from trying to be installed everytime i try to install something else? The package did partial install cause my printer works.

john@john-desktop:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cnijfilter-ip1800series (2.70-2) ...
invoke-rc.d: unknown initscript, /etc/init.d/cupsys not found.
dpkg: error processing cnijfilter-ip1800series (--configure):
 subprocess post-installation script returned error exit status 100
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-ip1800series
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by x33a on 2009-01-25
open synaptic and click on the broken filter on the left side.

then click edit -> fix broken packages.

---

### Post by lime4x4 on 2009-01-25
that didn't work. The i downloaded the deb package from a website i didn't use synaptic to install it

---

### Post by vhegos on 2009-01-25
To uninstall:  apt-get --purge remove <packagename>

---

### Post by lime4x4 on 2009-01-25
if i do that then i'm going to lose the drivers for my printer. I just want it to stop trying to install it

---

