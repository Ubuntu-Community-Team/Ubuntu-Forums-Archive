---
title: "Catalyst 9.1 trouble"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by 569874123 on 2009-02-08
Hi
While following this(manual part):
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)
I get the following error

```
diastopher@diastopher-desktop:~$ sh ati-driver-installer-9-1-x86.x86_64.run --buildpkg Ubuntu/intrepid 
Created directory fglrx-install.p11638
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.573...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/intrepid
Unable to install dpkg-dev.  Please manually install and try again.
./packages/Ubuntu/ati-packager.sh: 365: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.p11638

```

I have ubuntu 8.10 64 bit
Thanks

---

### Post by blueridgedog on 2009-02-08
Don't you need to sudo the install?

---

### Post by kdreimiller on 2009-02-08
yeah, try with sudo.  

also, id suggest following the installations directions on ati's website.

---

### Post by XanderCrews on 2009-02-08
I think that the problem that triggers the message you see is that you don't have dpkg-dev installed, and the ATI script needs it to build the .deb it uses to install the driver on your system.

```

sudo apt-get install dpkg-dev

```

XC

---

