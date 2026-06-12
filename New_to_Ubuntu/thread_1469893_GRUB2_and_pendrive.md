---
title: "GRUB2 and pendrive"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Lepaca on 2010-05-02
I have a pendrive with 2 partitions: 1st with FAT32 and 2nd with ext2.
I want to install GRUB2 but when I boot I obtain the error:
**no such disk**

at grub rescue prompt the ls command return an empty row
set command return:
[B]prefix=(hd0,2)/boot/grub
root=hd0,2[/B]

I changed prefix and root with hd0,1 hd1,1 hd1,2 and so on but same result


I installed grub on the 2nd partition from ubuntu 10.04 with these commands:

[B]grub-install --root-directory=/media/bootpart /dev/sdb
grub-mkconfig -o /media/bootpart/boot/grub/grub.cfg[/B]

where /dev/sdb is my pendrive and bootpart is the name of 2nd partition


please, help

---

### Post by oldfred on 2010-05-02
I have seen about 4 or 5  ways to boot USB pendrives.

I think you may need grub4dos version as that has the FAT partition first. Grub2 does not like to be installed to a partition and I do not know about USB keys.
[http://forums.fedoraforum.org/showthread.php?t=217113](http://forums.fedoraforum.org/showthread.php?t=217113)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I did this to have several ISOs on one USB flash drive.
MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)

Full Install:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

---

### Post by Lepaca on 2010-05-02
thanks oldfred for your reply, but I already looked at your links :(

I used same structure with GRUB 1 whit no problems

more info
if at the prompt of grub rescue, I type command **$root**, it return message:

**Unknown command 'hd0,2'**

---

### Post by oldfred on 2010-05-02
My usb key comes in as sdd the fourth disk as I have 3 internals. I would not think yours would be sda or (hd0)

---

