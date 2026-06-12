---
title: "Booting from usb memory"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by dougcumiskey123 on 2009-03-23
Is it possible to use the dual boot (Winxp/Ubuntu) to load/boot from a USB memory that is loaded with a start disk 8.10 amd64.

The reason I want to do this is that my laptop does not seem to have a USB boot in its bios and I want to use Ubuntu on the USB for experimenting without the need to reinstall on the HDD when I get it hopelessly wrong.

Doug

---

### Post by PenguinsFan on 2009-03-23
Yes, you can boot Ubuntu from a USB Flash Drive - but only if your BIOS supports booting from USB. It sounds like yours doesn't ?

Have you considered a live CD? If your BIOS doesn't support the USB option I'm sure it would still support booting from CD / DVD. You can use a live CD and run Ubuntu straight from the disc until you were ready to install.

Hope this helps! Good luck!

---

### Post by dougcumiskey123 on 2009-03-23
> **PenguinsFan said:**
> Yes, you can boot Ubuntu from a USB Flash Drive - but only if your BIOS supports booting from USB. It sounds like yours doesn't ?

Have you considered a live CD? If your BIOS doesn't support the USB option I'm sure it would still support booting from CD / DVD. You can use a live CD and run Ubuntu straight from the disc until you were ready to install.

Hope this helps! Good luck!

A live CD will not allow me to write to it! I want to try out changes to Ubuntu on a writeable media before making the changes to the HDD

---

### Post by primaxx on 2009-03-23
What about using wubi?
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
As far as I understand, you can both install and uninstall Ubuntu just like any other Windows-program.

Good luck! :-)

---

### Post by dougcumiskey123 on 2009-03-23
> **primaxx said:**
> What about using wubi?
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
As far as I understand, you can both install and uninstall Ubuntu just like any other Windows-program.

Good luck! :-)

On Wubi, yes I have tried that,  In both Winxp and Ubuntu and I get an error report, " It can't find autorun program" and 

"An error occurred while loading the archive.

(null)"


On the "in windows version, I will give it a try.

Doug.

---

### Post by dougcumiskey123 on 2009-03-24
When useing ubuntu via a live disk it seems that any changes made to ubuntu are not perminent so it has only limited use as a tool for testing new settings and programs. 

Can any one confirm this or have I got it wrong?

Doug.

---

### Post by nomes on 2009-07-10
how about these instructions.....way simpler  .... i think its for Jaunty only?   

[http://ubuntu-blog.com/how-to-install-ubuntu-jaunty-jackalope-on-a-pendrive](http://ubuntu-blog.com/how-to-install-ubuntu-jaunty-jackalope-on-a-pendrive)

---

### Post by oldfred on 2009-07-11
You can use GRUB to boot any device. So you can install Grub on your harddrive and configure it to boot your USB device. You also can use a CD to boot the USB drive.
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

