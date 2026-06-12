---
title: "Net install needs RTL8150"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by gratch6 on 2006-12-06
Installing Edgy on an old laptop with PCMIA card CD rom (not recognized and BIOS would not allow boot anyway), floppy works, no internal network card so the network card is USB - linksys USB100m which I know will work with RTL8150. I am installing with grub for DOS using a net install from:
[http://archive.ubuntu.com/ubuntu/dis...nstaller/i386/](http://archive.ubuntu.com/ubuntu/dis...nstaller/i386/)
which does not have the rtl8150 module (fatal error on modprobe - module not present).

Floppy boots to dos, grub runs, kernel loads but initial install fails at network setup due to the absence of this module.

I need some help to get past this point. Is there some way to get the module into the kernel?

---

### Post by FrodoB on 2006-12-06
Perhaps:

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by gratch6 on 2006-12-06
Thanks for the reply, but alas the CD rom is PCMIA and there is no known Linux driver (believe me I have looked). I can boot to a net install kernel, so booting is not the problem, it is the lack of the RTL8150 module that is the problem. At one point I was able to achieve a floppy net install of Debian on this Fujistu B142 laptop but somehow it got wasted and now I need to reinstall.

so - 
I can boot with Grub for Dos. I have a kernel for a net install but it lacks the module I need for the linksyst USB100m network device (that was working with debian). 

Other than repeating a debian net install (the details of which I would have to re-find) is there a way to install Ubuntu?

Do I need to compile a custom kernel?
Is there another source of a Ubuntu install package that I can copy and boot to?

Thanks!

---

### Post by FrodoB on 2006-12-07
Debian Etch claims to have your device's driver on the install floppies. You can get it from here:

[http://ftp.nl.debian.org/debian/dists/testing/main/installer-i386/rc1/images/floppy/](http://ftp.nl.debian.org/debian/dists/testing/main/installer-i386/rc1/images/floppy/)

It is very stable and I have had a machine running for over six months. You need at least the boot and root floppies I believe.

---

### Post by gratch6 on 2006-12-07
Thanks! I'll give it a go.

---

### Post by FrodoB on 2006-12-07
Let me know if that does it for you. Your device was one of the network device choices that I saw in one of the setup menus.

---

