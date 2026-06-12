---
title: "Can't Install bcm43xx-fwcutter"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by sjrlaw on 2007-06-29
I downloaded the package for this and extracted the files from the tarball.  However, the Synaptic Package manager and the apt-get command line utility can't find the package.  Help!  What am I doing wrong?

---

### Post by spd106 on 2007-07-01
Apt only understands .deb packages, so you will have to use one from the repositories, this is the latest version and is currently the simplest method to install. In order for it to retrieve the firmware automatically you will need an Internet connection. Though it also works off-line with known binary drivers too.  

Ubuntu 7.04 version [http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter)
Recommended Driver (SoftMAC) [http://linuxwireless.org/en/users/Drivers/bcm43xx#head-407dba1b3c9c70daf00cf6bd7cca6fe4e1783b67](http://linuxwireless.org/en/users/Drivers/bcm43xx#head-407dba1b3c9c70daf00cf6bd7cca6fe4e1783b67)

If you want to use the source from a tarball to build the utility then you will need the kernel- headers and build-essential packages plus their dependencies. Then you build the source with the usual make && sudo make install procedure. This method will take longer then installing a pre-built deb package, but gives you more control. [http://developer.berlios.de/project/showfiles.php?group_id=4547](http://developer.berlios.de/project/showfiles.php?group_id=4547)

---

