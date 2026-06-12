---
title: "Just Installed Scanner"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by daniell59 on 2010-07-28
I just installed an Epson Perfection V30 scanner.
How do I get Ubuntu to detect it?
Vista detected it after installing drivers.
Ubuntu 9.10
Thanks

---

### Post by sisco311 on 2010-07-28
You can download the driver & scanner utility from:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

Choose the model, OS, etc... then download and install: 
iscan-data_1.0.1-1_all.deb
and the 32bit or 64bit DEB packages (depending on which version are you using) for Ubuntu 8.10 or later.

---

### Post by daniell59 on 2010-07-28
> **sisco311 said:**
> You can download the driver & scanner utility from:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

Choose the model, OS, etc... then download and install: 
iscan-data_1.0.1-1_all.deb
and the 32bit or 64bit DEB packages (depending on which version are you using) for Ubuntu 8.10 or later.

Thanks
One thing is not clear however.
In respect to iscan-data_1.0.1-1_all.deb I do not see 64 bit listed.
Can I use the later packages?

Thanks again!

---

### Post by sisco311 on 2010-07-28
**all** at the end of the file name means *for all architectures*. You can install it on both 32-bit and 64-bit systems.

---

### Post by daniell59 on 2010-07-28
> **sisco311 said:**
> **all** at the end of the file name means *for all architectures*. You can install it on both 32-bit and 64-bit systems.

I just installed it. Should I boot the computer?

---

### Post by sisco311 on 2010-07-28
> **daniell59 said:**
> I just installed it. Should I boot the computer?

I don't think a reboot is necessary, but you may have to log out and log back in and unplug and plug in back the scanner. 

You can launch iscan from Applications -> Graphics -> Image Scan!

---

### Post by daniell59 on 2010-07-28
> **sisco311 said:**
> I don't think a reboot is necessary, but you may have to log out and log back in and unplug and plug in back the scanner. 

You can launch iscan from Applications -> Graphics -> Image Scan!

I guess I did something wrong. I don't see iscan.

---

### Post by daniell59 on 2010-07-28
Success
Don't ask me what I did. I am not sure. I downloaded a plug-in on the page you gave me, and it worked.
Thanks for your assistance.

---

### Post by jtarin on 2010-07-28
Do you have "Sane" installed? Issue the command ```
locate sane
```If not install it first before you look for anything else.

---

