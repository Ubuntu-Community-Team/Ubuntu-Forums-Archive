---
title: "RealTek 8821au Linux Driver 16.04: install.sh fails"
date: 2016-07-20
forum: Networking &amp; Wireless
---

### Post by navin.ms on 2016-07-20
Hello Experts,

I have been trying to install the RealTek 8821au driver on Ubuntu 16.04 Server OS but install.sh keeps failing. The RealTek WiFi comes as a USB adapter from 'Glam Hobby' manufacturer and was bought on Amazon [https://www.amazon.com/gp/product/B011T5IF06/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B011T5IF06/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1)   I have downloaded the latest drivers from [https://jumpshare.com/v/btbJdagrPEMKrFvZbjmg](https://jumpshare.com/v/btbJdagrPEMKrFvZbjmg) and following are the contents.

root@UbuntuServer1604:~/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51# ls
clean  core  hal  ifcfg-wlan0  include  Kconfig  Makefile  os_dep  platform  runwpa  wlan0dhcp
root@UbuntuServer1604:~/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51# 

When I run 'make' with superuser permissions, it fails with following message. I have not changed any file and running them as is. Running 'bash install.sh' available also fails exactly for the same following message.

root@UbuntuServer1604:~/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51# make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-31-generic/build M=/root/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-31-generic'
Makefile:340: scripts/Kbuild.include: No such file or directory
Makefile:622: arch/x86/Makefile: No such file or directory
/bin/bash: ./scripts/gcc-goto.sh: No such file or directory
Makefile:796: scripts/Makefile.kasan: No such file or directory
Makefile:797: scripts/Makefile.extrawarn: No such file or directory
make[1]: *** No rule to make target 'scripts/Makefile.extrawarn'.  Stop.
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-31-generic'
Makefile:1551: recipe for target 'modules' failed
make: *** [modules] Error 2
root@UbuntuServer1604:~/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51# 

Searched around in this forum and checked for most common issues but has not fixed my issue. Can someone please help?

Thank you,
Naveen.

---

### Post by chili555 on 2016-07-20
Did you try this?  [http://askubuntu.com/questions/752009/wireless-drivers-failing-to-build-when-make-command-is-run](http://askubuntu.com/questions/752009/wireless-drivers-failing-to-build-when-make-command-is-run)

---

