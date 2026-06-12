---
title: "Installing from an external drive"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by joshnielsen on 2010-12-16
i already posted this somewhere but im a noob and didnt see this section lol. What im trying to do is install ubuntu from an external drive but i dont know how to. i tried extracting the .iso to the drive and then booting from the drive but that didnt work. any help?

---

### Post by Rex Bouwense on 2010-12-16
Welcome.  Just having the ISO copied to an external drive will not install.  You must burn that ISO to a CD, USB flash drive, and I would assume an external hard drive.  Before you do that check the download.  Do an MD5Sum.
  
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You can then burn the ISO to your CD or whatever device that you are going to use to boot your computer.  
Change the boot order in the BIOS so that the device that has the burned ISO will boot first.  Enjoy.

---

### Post by joshnielsen on 2010-12-16
> **Rex Bouwense said:**
> Welcome.  Just having the ISO copied to an external drive will not install.  You must burn that ISO to a CD, USB flash drive, and I would assume an external hard drive.  Before you do that check the download.  Do an MD5Sum.
  
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You can then burn the ISO to your CD or whatever device that you are going to use to boot your computer.  
Change the boot order in the BIOS so that the device that has the burned ISO will boot first.  Enjoy.

i did burn the iso to the external hard drive but when i went to boot it it said missing BOOTMGR.

---

### Post by Rex Bouwense on 2010-12-16
I just did a google search of "missing bootmgr" and found a bunch a information.  You can do the same or look at:

[http://ubuntuforums.org/showthread.php?t=1384362](http://ubuntuforums.org/showthread.php?t=1384362)

---

### Post by C.S.Cameron on 2010-12-16
Startup Disk Creator from the Live CD will install to an external USB drive and make it bootable.
You will be able to use it to install to an internal drive.

---

### Post by joshnielsen on 2010-12-16
> **C.S.Cameron said:**
> Startup Disk Creator from the Live CD will install to an external USB drive and make it bootable.
You will be able to use it to install to an internal drive.

it doesnt pick up my external drive as a flash drive so i cant use that.

---

### Post by sgosnell on 2010-12-16
Use unetbootin.  Be careful, and make very sure you select the correct drive to burn the .iso to.

---

### Post by C.S.Cameron on 2010-12-17
> **joshnielsen said:**
> it doesnt pick up my external drive as a flash drive so i cant use that.

Hummm, usb-creator worked for me with an external USB HDD just fine, are you using 10.10?

Another method used grub2 to boot the iso file.
MultiBootUSB is one example.

---

### Post by Com_2_Reset on 2010-12-18
Hello,

1- The following link will explain how to burn Ubuntu to CD or create USB Drive:
 [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
2- Remember: 
         If you want to burn to CD, then configure your Laptop or Pc to boot from CD. 
         If you want to create USB drive, then configure your laptop or pc to boot from USB. 

Have fun

---

