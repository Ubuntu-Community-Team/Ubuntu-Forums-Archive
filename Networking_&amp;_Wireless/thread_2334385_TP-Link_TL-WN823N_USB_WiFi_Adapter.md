---
title: "TP-Link TL-WN823N USB WiFi Adapter"
date: 2016-08-19
forum: Networking &amp; Wireless
---

### Post by adam17 on 2016-08-19
Hi all,

Just bought a TP-Link TL-WN823N USB WiFi Adapter and having some serious problems getting it to work.

I have tried downloading the drivers from TP-Link and following the instructions "sudo make" , "sudo make install" etc but keep getting an error during this process:

cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/adam/Downloads/core/rtw_debug.o' failed
make[2]: *** [/home/adam/Downloads/core/rtw_debug.o] Error 1
Makefile:1403: recipe for target '_module_/home/adam/Downloads' failed
make[1]: *** [_module_/home/adam/Downloads] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-31-generic'
Makefile:731: recipe for target 'modules' failed
make: *** [modules] Error 2

and then when typing the second command the following, presumable as the first stage has failed:

"******************************************"
"NO SKRC,we will use default KSRC"
"******************************************"
install -p -m 644 8192cu.ko  /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/
install: cannot stat '8192cu.ko': No such file or directory
Makefile:737: recipe for target 'install' failed
make: *** [install] Error 1

Has anyone managed to install one of these adapters nothing online seems to be very clear on how to get this working, I have just installed a fresh Ubuntu 16.04 LTS.

Any help greatly appreciated.

Thanks Adam.

---

### Post by juanmfc123 on 2016-12-05
I have been having the same problem and have looked in almost every ubuntu forum for answer but no one seems to have it.  I saw your post and noticed it is fairly old and wanted to know if since then you have found an answer to this problem.  I have tried the git solutions and installing numerous packages but nothing seems to work. please let me know if yo found a way around the problem

[https://askubuntu.com/questions/813443/tp-link-tl-wn823n-unable-to-connect-to-network](https://askubuntu.com/questions/813443/tp-link-tl-wn823n-unable-to-connect-to-network) found the solution

---

