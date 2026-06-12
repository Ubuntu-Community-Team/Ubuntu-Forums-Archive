---
title: "CReating a USB boot drive manually"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-10
Ive tried using the utility unetbootin and the startup disk creator to create a USB flash drive bootable with no success,

is there a manual way to do it ?

---

### Post by oldfred on 2011-06-10
Does your computer have bootable USB ports. Only computers in the last 4-5 years have BIOS that allow booting from the USB2 ports.

Most users follow the directions on the Ubuntu download page.
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you want a totally manual way, you can install grub2 to a USB flash drive, edit grub.cfg to loop mount an ISO file directly and just copy the ISO file to the flash drive. This uses grub2 not syslinux to boot.

Some have created scripts to automate the ISO install. You can have as many ISOs on one flash drive as it will hold.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by kalimojo on 2011-06-10
yes the USB port is bootable . at least the KINGSTON USB drive shows up in the BIOS and the USB pen drive tries to boot and fails with an error COM32R not found,

---

### Post by Joe of loath on 2011-06-10
sudo dd if=/path/to/iso of=/dev/sdx (replace X with the drive letter, but don't add the 1 after it).

---

### Post by kalimojo on 2011-06-10
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)


worked a treat, thanks

---

