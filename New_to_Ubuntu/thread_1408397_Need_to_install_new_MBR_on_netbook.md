---
title: "Need to install new MBR on netbook"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-02-16
Greetings,

I broke my boot on my Dell Mini 9 last night by having the bright idea of trying to install Xubuntu 9.10 on a SDHC card and installing grub on my hard drive, thinking it would allow me to choose between the hard drive (win7 pro) and the SDHC card (xubuntu).

At this point, I don't care about the Xubuntu installation; I need to be able to boot Windows back up again, though.

Should I try to use grub to just get Windows to work (question is, how? i'm extremely limited in this subject), or should I try to use Windows' Recovery Console to create a new Windows MBR?

The only problem with the Win7 DVD solution is that I only have a DVD of Windows 7, and with no optical drive, I'm unsure of the procedure here.

Thanks,

--Red

---

### Post by oldfred on 2010-02-16
From Ubuntu you can download lilo and install a basic windows boot loader that may work.

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

or

[http://www.blogsdna.com/2016/how-to-install-windows-7-from-usb-drive-without-windows-7-iso-dvd.htm](http://www.blogsdna.com/2016/how-to-install-windows-7-from-usb-drive-without-windows-7-iso-dvd.htm)

It would be best to have the windows boot loader on the internal drive and grub on the external. And have BIOS boot first from the external. That way if the  external is not plugged in it will default to the internal. Grub should also find the windows install and let you choose to boot that if the external is plugged in.

---

