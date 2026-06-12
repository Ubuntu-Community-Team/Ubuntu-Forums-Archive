---
title: "Boot Ubuntu 11.04 from USB"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by solwatts on 2011-08-23
Hello,
I've read on the Ubuntu website that you can BOOT ubuntu from a flash drive.  My question is, can you RUN Ubuntu COMPLETELY from a USB flash drive? As in, saving documents, installing applications, and using Ubuntu from the Flash drive, not using it to test or install on to a PC.

---

### Post by skatinjj on 2011-08-23
Use the livecd to install it just as you would to a internal HDD.

---

### Post by oldfred on 2011-08-23
It is a regular install but like any second drive you want to manually install so you can install the grub2 boot loader to the MBR of the flash drive. Minimal install is now over 4GB, so you need at least 8GB. I installed to a 16GB flash but used only a 8GB partition. Not speedy due to flash & USB speeds but functional. You do also want to change a few settings to minimize writes.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by zengrz on 2011-08-23
You would probably not want to do that, even if you can.

---

