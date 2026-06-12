---
title: "Mobile Partner Linux Driver 4.19.19.00.tar.gz on ubuntu 15.1 Wily Error:"
date: 2016-03-02
forum: Networking &amp; Wireless
---

### Post by sundar3 on 2016-03-02
[COLOR=#000000]I have new installation of ubuntu 15.1 Wily Werewolf on which I am trying to install the Mobile Partner Linux Driver 4.19.19.00 and get the below error on the terminal[/COLOR]


[COLOR=#000000]Your help would be greatly appreciated:[/COLOR]


[COLOR=#000000]DRIVER COPY START STA_PATH_FLAG=. STA_PATH_FULL=/home/sundararaman/Desktop/driver/install START_PATH_DRIVER=/home/sundararaman/Desktop/driver CURRENT install from ./install INSTALL_PATH is not set ,auto install INSTALL_PATH=/usr/local/Mobile_Partner INSTALL_PATH is another path rm /usr/local/Mobile_Partner/driver DRIVER COPY END have usb_modeswitch rules to HUAWEI DataCard: COUNT=0 ls: cannot access /dev/ttyUSB?: No such file or directory ttyUSB%n not exist,ok rmmod: ERROR: ../libkmod/libkmod-module.c:793 kmod_module_remove_module() could not remove 'cdc_ether': No such file or directory rmmod: ERROR: could not remove module cdc_ether: No such file or directory rmmod: ERROR: ../libkmod/libkmod-module.c:793 kmod_module_remove_module() could not remove 'usbnet': No such file or directory rmmod: ERROR: could not remove module usbnet: No such file or directory rmmod: ERROR: ../libkmod/libkmod-module.c:793 kmod_module_remove_module() could not remove 'hw_cdc_driver': No such file or directory rmmod: ERROR: could not remove module hw_cdc_driver: No such file or directory make -C src/ clean make[1]: Entering directory '/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src' rm -rf *.o *.ko ~ core .dep* ..d ..cmd *.mod.c *.a .s ..flags .tmp_versions Module.symvers Modules.symvers .order /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/add_header.sh "clean" "/lib/modules/4.2.0-16-generic/build/include/linux/usb" rmmod -f hw_cdc_driver rmmod: ERROR: ../libkmod/libkmod-module.c:793 kmod_module_remove_module() could not remove 'hw_cdc_driver': No such file or directory rmmod: ERROR: could not remove module hw_cdc_driver: No such file or directory Makefile:37: recipe for target 'clean' failed make[1]: [clean] Error 1 make[1]: Leaving directory '/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src' Makefile:30: recipe for target 'clean' failed make: * [clean] Error 2 make -C src/ modules make[1]: Entering directory '/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'[/COLOR]


[COLOR=#000000]/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/add_header.sh "modules" "/lib/modules/4.2.0-16-generic/build/include/linux/usb"[/COLOR]
[COLOR=#000000]make -C /lib/modules/4.2.0-16-generic/build SUBDIRS=/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src modules make[2]: Entering directory '/usr/src/linux-headers-4.2.0-16-generic' CC [M] /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: In function ‘hw_cdc_probe’: /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:2718:9: error: implicit declaration of function ‘dbg’ [-Werror=implicit-function-declaration] dbg ("can't kmalloc dev"); ^ cc1: some warnings being treated as errors scripts/Makefile.build:264: recipe for target '/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o' failed make[3]: * [/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o] Error 1 Makefile:1398: recipe for target 'module/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src' failed make[2]: [_module_/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src] Error 2 make[2]: Leaving directory '/usr/src/linux-headers-4.2.0-16-generic' Makefile:32: recipe for target 'modules' failed make[1]: [modules] Error 2 make[1]: Leaving directory '/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src' Makefile:27: recipe for target 'modules' failed make: * [modules] Error 2 make -C src/ install make[1]: Entering directory '/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'[/COLOR]


[COLOR=#000000]install -m 744 -c hw_cdc_driver.o /lib/modules/4.2.0-16-generic/kernel/drivers/usb/net[/COLOR]
[COLOR=#000000]depmod -a[/COLOR]
[COLOR=#000000]modprobe hw_cdc_driver[/COLOR]
[COLOR=#000000]/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/add_header.sh "install" modprobe hw_cdc_driver modprobe: FATAL: Module hw_cdc_driver not found. Makefile:43: recipe for target 'install' failed make[1]: * [install] Error 1 make[1]: Leaving directory '/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src' Makefile:33: recipe for target 'install' failed make: * [install] Error 2[/COLOR]

[COLOR=#000000]Install NDIS driver failed. The compiling environment is not all ready. Please check gcc, make and kernel buid(/lib/modules/4.2.0-16-generic/build) to be all installed? Now please enter any key to finish other installations.[/COLOR]


[COLOR=#000000]NDIS is disabled, and only Modem can be used. USBSERIAL_TARGET_PATH =[/COLOR]

[COLOR=#000000]..[/COLOR]

[COLOR=#000000]Thanks, sundar[/COLOR]

---

