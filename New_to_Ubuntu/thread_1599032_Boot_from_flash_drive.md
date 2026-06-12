---
title: "Boot from flash drive"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by dimhenw on 2010-10-17
I just download latest (ubuntu-10.10-desktop-i386) version and installed onto a 8gb flash drive using the installer suggested (Universal-USB-Installer-1.8.0.5).

Added 4gb persistence.

Each time i boot from the flash drive all i get is the following lines of code

[http://onfinite.com/libraries/1628267/271.jpg](http://onfinite.com/libraries/1628267/271.jpg)

The pic is too big for the thread and I'm kinda clueless at thumbnails.

I have had previous installations of ubuntu installed on hard drive(no issues), but opted for flash drive since I'm running out of space.

Any help would be greatly appreciated.

D. ;)

---

### Post by linux-hack on 2010-10-17
The lines you can see in the picture is because the flash drive has brocken blocks.. But this meens that you need to reinstall you key and make sure it works... or try making a ```
fsck
``` on the drive from another system.

---

### Post by Hippytaff on 2010-10-17
I had loads of problems with bootable usb...you could do a few things to check the iso is fine...like check the md5sum [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

but I only wanted to run the live environment to check hardware compatibility so did a live cd, then installed it once I knew i wouldn't encounter hardware issues

---

### Post by dimhenw on 2010-10-17
Thx for quick reply and will try that. ;)

---

### Post by linux-hack on 2010-10-17
just let us know if it works and put a RESOLVED in the title . So other people with the same problem will be able to do the same thing.

---

