---
title: "Wireless card doesn't work in Edgy"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by rpasell on 2006-11-04
I'm new to Ubuntu, but not Linux in general, though it's been a while since I've used any distro.  I have an Acer Aspire 5102 with an AMD Turion 64 X2 TL-50, 1G DDR RAM, ATI Radeon Xpress 1100.  Dual booting XP and Edgy using GRUB.  Now the relevant stuff:

I can't get the built in Broadcom 802.11g wireless card to work in Edgy.  It shows up in Network Manager as Wireless Connection (eth1), it allows me to configure it, and activate it, but it never works.  Bringing up a terminal session and issuing ifconfig shows the LAN port and a connection called wifi0 which I would normally assume would be the built in card, but it never acquires an address.  eth1 does not show up when ifconfig is run.  In device manager the interface shows up as BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.

I've searched the forum for answers, and have seen a few posts regarding this hardware, but nothing that helped solve my issue.  I appreciate any responses.  Thanks

---

### Post by justintime32 on 2006-11-04
The reason it doesn't work is because you didn't install the firmware (which cannot be shipped in Ubuntu due to licensing reasons).

If you want it to work as easily as possible, just download [this]("http://ubuntu.cafuego.net/pool/dapper-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb") package onto a CD or a USB thumb drive (or even a floppy if you want) then install it on Ubuntu.

However, that uses the highly experimental driver which is currently limited to 11 MB/s. If you want to get full 54 MB/s speed, you need to install ndiswrapper. You should follow [this]("http://ubuntuforums.org/showthread.php?t=197102") guide.

---

### Post by rpasell on 2006-11-08
Sorry it's taken me so long to test this.  Following the instructions here

[http://ubuntuforums.org/showpost.php?p=1469830&postcount=357](http://ubuntuforums.org/showpost.php?p=1469830&postcount=357)

when I issue:

rob@ACERlaptop:~/Desktop/acer_acpi-0.3$ sudo modprobe acer_acpi

I get:

FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-generic/extra/acer_acpi.ko): No such device

I've tried copying the .ko file to that directory manually with no success.

Any ideas?

---

### Post by Arabian on 2007-02-05
It works alright with me with DesktopBSD 1.6-RC1

---

