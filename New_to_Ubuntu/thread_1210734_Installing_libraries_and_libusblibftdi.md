---
title: "Installing libraries and libusb/libftdi"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by HABalloonGirl on 2009-07-11
Hi all,

I've installed libusb and libconfuse and the development files with the package manager and they seem to be in the right places.  I've also added usb.h to /usr/include.  I'm trying to build libftdi.  I've installed all the appropriate files in the library directory in /usr/lib.  In the main part of the ftdi library I've done ./configure, make, and make install, all of which seem to work.  However, when I tried #include <ftdi.h> in another program, gcc says the file doesn't exist.  (its been put in /usr/include)  Not only that, when I go into the src folder of the libftdi files and try make ftdi, there are all kinds of errors because it can't find the link to libusb. 

 Have I done something funny in installing my libraries?  The first 2 were just with the package manager and I installed libftdi with a .tar.gz file.  I need libftdi to deal with the newer 4232H chip.  

Thanks!

Connie

---

