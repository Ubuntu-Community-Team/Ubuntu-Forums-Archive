---
title: "creating a dual boot usb stick"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by trbone on 2011-04-18
This may be a really stupid question, but I did a search and couldn't find any answers...

I want my 4Gb USB stick to have 2 different linux options to boot from. 

I have separated it into 2 partitions, and installed a different distro on each partition (pupeee on one and deft on the other).

However when I try to boot from the USB stick it will only boot from one or the other partition. How do I make it so that it gives me a choice of which partition to boot from?

Thanks

---

### Post by Megaptera on 2011-04-18
Is this guide any help?

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)

". Here is one way to create a Multiboot USB Flash Drive from a running Ubuntu (I used the Live CD)."

---

### Post by trbone on 2011-04-18
> **Megaptera said:**
> Is this guide any help?

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)

". Here is one way to create a Multiboot USB Flash Drive from a running Ubuntu (I used the Live CD)."

Thanks. It is a little help. Unfortunately the distros I am using aren't covered in this tutorial. I tried following the 

"Adding an Unlisted ISO: To try ISO Files that are not yet listed, use the existing menuentry examples in /boot/grub/grub.cfg and append any options normally found in the distributions syslinux.cfg file on the "append" line to the "linux" line of the menu entry."

but as I have zero programming experience when I looked at /boot/grub/grub.cfg i have no idea what I would do to it to follow these instructions.

I was kinda hoping that there was some easy way to do this (like involving a gui and pointing and clicking). I might have to give up and just change the partition that is allocated as the boot partition when I want to use the other distro...

---

### Post by oldfred on 2011-04-18
Do you want to boot multiple ISOs or have full installs?

ISO
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

multicd.sh - combine Linux ISOS into one CD
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)


If you have full installs, then what boot loader did you install to the MBR, grub, grub2 or lilo? (not familar with the distributions you mentioned). Just edit the menu of the grub that is in control to boot the other.

---

### Post by gordintoronto on 2011-04-18
Have a look at Full Circle Magazine, issue 45, page 13. It's a free download.

---

### Post by beew on 2011-04-18
If you are using Ubuntu multisystem is the tool for you. It creates multi-boot live usbs from isos and supports many distros. It is very easy to use with an intuitive gui.

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

The webpage is in french but the actual program is in English.

---

### Post by trbone on 2011-04-19
> **beew said:**
> If you are using Ubuntu multisystem is the tool for you. It creates multi-boot live usbs from isos and supports many distros. It is very easy to use with an intuitive gui.

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

The webpage is in french but the actual program is in English.

This did the job nicely... Thanks.

---

