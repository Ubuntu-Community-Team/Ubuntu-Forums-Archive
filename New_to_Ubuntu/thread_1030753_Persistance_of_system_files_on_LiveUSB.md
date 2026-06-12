---
title: "Persistance of system files on LiveUSB"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by rCXer on 2009-01-04
I've been running Ubuntu 8.10 off a USB pendrive using  [these](http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/) instructions.  While most files are persistent, it does not retain changes to system files like "/etc/fstab".  Is there any way to change this? Thanks!

---

### Post by extensa30 on 2009-01-04
I've got something like the same issue: I've foloowed the same instructions, but nothing works: from saving the wifi settings, or even the installed nvidia drivers. Any help?

---

### Post by rCXer on 2009-01-04
Glad to hear I'm not the only one.  I might be in a slightly better situation ;) because my wireless settings and all programs installed are persistent between sessions. I really hope someone replies.  

Does anyone know a way to install Ubuntu to a pendrive as if it was a hard drive (without casper-rw)?

---

### Post by Captain_tux on 2009-01-05
I installed 8.10 yesterday to an 8GB thumb drive using the instructions provided in [Linux Format Magazine]("http://www.linuxformat.co.uk/covers/114-big.jpg")... I only used it for a couple of hours, but everything seems to be working fine. I'll play with it some and report back...

---

### Post by wizard10000 on 2009-01-05
Intrepid has its own utility for creating a bootable flash drive - you can find it in System --> Administration --> Make a USB startup disk.  I'm pretty sure a live CD is required.

I've created the bootable disk using the utility on the live CD and the installer asks you whether you want to reserve some space for files to be written to the flash drive - and I'm guessing in the grand scheme of things this will probably be the only supported configuration.

Anyway, I bought a 4gb flash drive, partitioned it into two 2gb partitions, formatted both as FAT32 and Intrepid happily installed on partition #1.

Hope this helps -

---

