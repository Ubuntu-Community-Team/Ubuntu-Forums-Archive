---
title: "New HD, new to Ubuntu"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by RJ Scott on 2010-12-11
Hello all! I've got a bit of a problem. I've just had to replace the hard drive in my laptop (old one broke), and the new drive, although physically installed, is completely raw (no OS whatsoever). Will the Wubi installer work from a USB drive if the HD has no OS?

---

### Post by sikander3786 on 2010-12-11
Welcome to the forums :-)

If you plan to put Ubuntu as the sole OS on your new HDD, you don't need Wubi at all. It is just intended to test Ubuntu from a Windows system.

What you need at the moment is an Ubuntu ISO image, a working computer to create the USB drive and definitely a 1GB or bigger USB drive itself.

How to burn Live USB:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

You'll need to change your Bios boot order to boot from the USB drive.

---

### Post by ajgreeny on 2010-12-11
> **RJ Scott said:**
> Hello all! I've got a bit of a problem. I've just had to replace the hard drive in my laptop (old one broke), and the new drive, although physically installed, is completely raw (no OS whatsoever). Will the Wubi installer work from a USB drive if the HD has no OS?
No it will not work as wubi is for installing Ubuntu within Windows; no Windows, no wubi Ubuntu.

You can, however, and will probably be much better off either borrowing a live CD from somebody who already has one, and partitioning the whole disk as a _U_buntu system, or doing what sikander says above.  See the link below about separate home for details.

[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

