---
title: "invalid argument opening scanner"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Dibbling Dave on 2009-03-27
Hello, I have a problem opening my Epson 3490 scanner with XSane, I get the following error message:

Failed to open device 'snapscan:libusb:003:006':
Invalid argument

I've read this thread [http://ubuntuforums.org/showthread.php?t=1099482&highlight=xsane](http://ubuntuforums.org/showthread.php?t=1099482&highlight=xsane) but didn't really understand. 

Any help appreciated. Dave.

---

### Post by Dibbling Dave on 2009-03-28
I have updated the libsane-extras

dave@dave-desktop:~$ sudo apt-get install libsane-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsane-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libtwolame0 libdca0 libdvbpsi4 libenca0 libiso9660-5 liblua5.1-0 libvcdinfo0
  libebml0 libmatroska0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$ 

I still cannot open my scanner and get the same message. Any ideas what to do now, Dave.

---

