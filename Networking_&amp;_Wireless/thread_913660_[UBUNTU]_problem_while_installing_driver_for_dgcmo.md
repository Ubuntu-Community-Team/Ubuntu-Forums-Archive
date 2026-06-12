---
title: "[UBUNTU] problem while installing driver for dgcmodem!!!!!! help!!!"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by parvathy on 2008-09-08
i used scanModem to get the information about the modem in my laptop. it suggested the driver for dgcmodem and the suggested version is  dgcmodem-7.68.00.12full_k2.6.24_16_generic_ubuntu_i386.deb.zip .but i couldn't find the exact version so i downloaded one which matches my kernel -dgcmodem_1.07_k2.6.24_16_generic_ubuntu_i386.deb .



when i installed that it showed an error like this


 dpkg: error processing /home/amma/Desktop/dgcmodem_1.07_k2.6.24_16_generic_ubuntu_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:



so what should i do now? is there any other packages for my modem?

---

### Post by prshah on 2008-09-08
> **parvathy said:**
> 
 dpkg: error processing /home/amma/Desktop/dgcmodem_1.07_k2.6.24_16_generic_ubuntu_i386.deb (--install):
 package architecture (i386) does not match system (amd64)


You are probably running the amd64 version of ubuntu; check with ```
uname -a
```

---

### Post by parvathy on 2008-09-08
thank you for your reply.
i tried uname 
the output is given below


Linux amma-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

can you infer anything from this.

---

### Post by prshah on 2008-09-08
> **parvathy said:**
> 
Linux amma-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 [color=red]x86_64[/color] GNU/Linux

This means you are running Ubuntu 64-bit; either change to 32 bit (i386), or get the dgcmodem package that is suitable for 64-bit architecture.

---

### Post by parvathy on 2008-09-09
thank you for your timely reply.i checked for device driver which satisfies x86_64 system architecture. but i couldn't find one. but i could find one which was said to be compatible with most of the system architecture.dgc-modem_1.07.tar. i could install it. but after that i couldn't configure the modem. when i checked ttyACM0 file, it showed the error that no device found.


i'm a beginner in ubuntu . and i'm now fed up with these errors.

can u help me to figure it out....

---

### Post by rickfitz on 2008-10-03
Don't know if this will help, but version 1.08 is now available on [www.linuxant.com](www.linuxant.com)
I've installed on 32-bit Hardy with no problem using a pre-compiled driver, but these are only available for 32-bit. With 64-bit you must compile your own...
Good luck!

---

