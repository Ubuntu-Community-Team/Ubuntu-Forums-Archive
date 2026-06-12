---
title: "Installing bradcom sta from CD: Dependency not satisfiable: gcc."
date: 2011-01-02
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2011-01-02
Hey all, 
   I've used Ubuntu for  several months now, and am wanting to try Kubuntu. 

   I just installed it, and since I don't have a wired connection available here, I am trying to install the broadcom STA driver to get my wireless working. 

   On any previous Ubuntu install this has worked however, when installing a few of the packages namely dkms, and bcmwl as outlined here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)  ```
Navigate the install media and install the packages listed below by double clicking or navigate the install media and install these packages consecutively in a terminal (under the desktop menu Applications > Accessories > Terminal):

../pool/main/d/dkms

:/dkms/$ sudo dpkg -i dkms*
../pool/main/p/patch

:/patch/$ sudo dpkg -i patch*
../pool/main/f/fakeroot

:/fakeroot/$ sudo dpkg -i fakeroot*
../pool/restricted/b/bcmwl

:/bcmwl/$ sudo dpkg -i bcmwl-kernel-source*

``` 
I get the folowwing error in the GDebi Package Installer when installing dkms and bcmwl: ```
Error:Dependency is not satisfiable: gcc
```

Any suggestions as I cant imaging gcc is not in place.

---

### Post by cariboo on 2011-01-02
You also need to install build-essential, in order to install the STA drivers. I managed to install the drivers by mounting my usb thumbdrive as a cdrom, then marking  bcmwl-kernel-source for installation, it also installed all the needed dependencies.

Of course if you have a router, it is probably easier to just to hook up an ethernet cable to install the driver.

---

