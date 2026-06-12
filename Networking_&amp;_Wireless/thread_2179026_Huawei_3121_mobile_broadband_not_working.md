---
title: "Huawei 3121 mobile broadband not working"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by zerocool2 on 2013-10-06
i have purchase **Huawei 3121 mobile broadband** , but i am facing problem to installation of driver.

i follow the step given on [http://www.huaweidevice.co.in/Downloads/Linux-Installation-User-Guide.pdf](http://www.huaweidevice.co.in/Downloads/Linux-Installation-User-Guide.pdf)......

i downloaded respective driver which is mentioned there **HUAWEI Data Cards Linux Driver.zip,**i extract the folder and i got a driver folder , i move the driver folder in /root/Desktop.

after that i perform these commands
[B]cd /root/Desktop/driver
#: pwd
#:/root/Desktop/driver

#:./install /root/Desktop[/B]

after doing this some error occur .....

root@zerocool-Lenovo-G580:~/Desktop/driver# ./install /root/Desktop
DRIVER COPY START
STA_PATH_FLAG=.
STA_PATH_FULL=/root/Desktop/driver/install
START_PATH_DRIVER=/root/Desktop/driver
CURRENT install from ./install
INSTALL_PATH=/root/Desktop
DRIVER COPY END
have usb_modeswitch rules to HUAWEI DataCard: COUNT=1
RULESFILE =/lib/udev/rules.d/40-usb_modeswitch.rules
COUNT_START=1
COUNT_END=0
3
ttyUSB%n COUNT=3
3-4:1.3 unbind and bind option
COUNT_END=2
3-4:1.2 unbind and bind option
COUNT_END=1
3-4:1.0 unbind and bind option
COUNT_END=0
libkmod: ERROR ../libkmod/libkmod-module.c:753 kmod_module_remove_module: could not remove 'cdc_ether': No such file or directory
Error: could not remove module cdc_ether: No such file or directory
libkmod: ERROR ../libkmod/libkmod-module.c:753 kmod_module_remove_module: could not remove 'usbnet': Resource temporarily unavailable
Error: could not remove module usbnet: Resource temporarily unavailable
libkmod: ERROR ../libkmod/libkmod-module.c:753 kmod_module_remove_module: could not remove 'hw_cdc_driver': No such file or directory
Error: could not remove module hw_cdc_driver: No such file or directory
make -C src/ clean
make[1]: Entering directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
/root/Desktop/driver/ndis_driver/ndis_src/src/add_header.sh  "clean" "/lib/modules/3.8.0-31-generic/build/include/linux/usb"
rmmod -f hw_cdc_driver
libkmod: ERROR ../libkmod/libkmod-module.c:753 kmod_module_remove_module: could not remove 'hw_cdc_driver': No such file or directory
Error: could not remove module hw_cdc_driver: No such file or directory
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
make: *** [clean] Error 2
make -C src/ modules
make[1]: Entering directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
#/root/Desktop/driver/ndis_driver/ndis_src/src/add_header.sh  "modules" "/lib/modules/3.8.0-31-generic/build/include/linux/usb"
make -C /lib/modules/3.8.0-31-generic/build SUBDIRS=/root/Desktop/driver/ndis_driver/ndis_src/src modules
make[2]: Entering directory `/usr/src/linux-headers-3.8.0-31-generic'
  CC [M]  /root/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o
/root/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: In function &#8216;hw_cdc_probe&#8217;:
/root/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:2718:9: error: implicit declaration of function &#8216;dbg&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/root/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o] Error 1
make[2]: *** [_module_/root/Desktop/driver/ndis_driver/ndis_src/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.8.0-31-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
make: *** [modules] Error 2
make -C src/ install
make[1]: Entering directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
#install -m 744 -c hw_cdc_driver.o /lib/modules/3.8.0-31-generic/kernel/drivers/usb/net
#depmod -a
#modprobe hw_cdc_driver
/root/Desktop/driver/ndis_driver/ndis_src/src/add_header.sh  "install"
modprobe hw_cdc_driver
FATAL: Module hw_cdc_driver not found.
make[1]: *** [install] Error 1
make[1]: Leaving directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
make: *** [install] Error 2


Install NDIS driver failed.
The compiling environment is not all ready.
Please check gcc, make and kernel buid(/lib/modules/3.8.0-31-generic/build) to be all installed?
Now please enter any key to finish other installations.
 NDIS is disabled, and only Modem can be used.
USBSERIAL_TARGET_PATH = 
ACM_TARGET_PATH = 
ADDRUNLEVEL=/etc/rc4.d
&#8216;/etc/rc4.d/S99runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
&#8216;/etc/rc4.d/K10runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
ADDRUNLEVEL=/etc/rc3.d
&#8216;/etc/rc3.d/S99runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
&#8216;/etc/rc3.d/K10runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
ADDRUNLEVEL=/etc/rc5.d
&#8216;/etc/rc5.d/S99runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
&#8216;/etc/rc5.d/K10runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
ADDRUNLEVEL=/etc/rc2.d
&#8216;/etc/rc2.d/S99runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
&#8216;/etc/rc2.d/K10runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
qmi_wwan interface not exist,ok



what i do for installing driver, thank you in advance......

---

### Post by varunendra on 2013-10-06
Welcome to the forums zerocool2 !,

Why are you using the root account? It is almost never required and can break your system in a number of ways unless you are quite an expert in Linux and are absolutely aware what you are doing. By your inability to recognize the cause of the above errors, it does not look like you are an expert yet. So I'd strongly recommend to use normal account for everything you need. Please take some time to read this : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

About the driver, let's first make sure if you even need a third party driver. Please post the output of -
```
lsusb
```
while the modem is plugged-in. Most GSM/3G modems are natively supported, so you may not need to install an external driver.

By the way, the errors indicate you may not have linux-headers and/or build-essential installed -
```
sudo apt-get install linux-headers-generic build-essential
```

**PS:**
Please always use '**Code**' box to post commands & terminal outputs. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by zerocool2 on 2013-10-07
sorry for inconvenience regarding my post,,,,, i am a new user and i have not more idea how to post things.

as you mentioned above i run this command and respective package has been installed

sudo apt-get install linux-headers-generic build-essential
and result for :  sudo lsusb

zerocool@zerocool-Lenovo-G580:~$ sudo lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 003 Device 007: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 001 Device 004: ID 5986:0294 Acer, Inc 
Bus 002 Device 003: ID 04ca:2003 Lite-On Technology Corp. 
Bus 002 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader

---

### Post by zerocool2 on 2013-10-07
thank you sir it is working now , but please resolve this issue also,,,,,,


when i use it in windows 8, a software called mobile partner is installed so that i can use its features like calling ,sms, and many,,,,

How to get graphical mode like in windows ?

please resolve this issue i will very thank  full to you.....

---

### Post by varunendra on 2013-10-08
> **zerocool2 said:**
> when i use it in windows 8, a software called mobile partner is installed so that i can use its features like calling ,sms, and many,,,,

How to get graphical mode like in windows ?

I haven't installed Mobile Partner in Ubuntu after 10.04, so it's a long time now. But you may try this solution, looks promising : [http://askubuntu.com/a/323397](http://askubuntu.com/a/323397)

However, please also read the comments below it -
> is the most forward way to install Mobile Partner, however, I would advise against it. It is full of bugs and compromises the security of your system. The most important one is that it adds ALL ALL=(ALL) NOPASSWD:ALL to your sudoers file which allows to run all sudo commands without password!

I can personally confirm that of the three different versions of it I tried (long before), it even ran the browser as root which is a **[COLOR="#FF0000"]HUGE security risk[/COLOR]**. If you close the one opened by Mobile Partner, and open another one directly, it won't connect to internet.

So if you try above, please confirm if you face the same issue and also post back the output of -
```
sudo cat /etc/sudoers
```
..so that we can correct at least the "ALL ALL=(ALL) NOPASSWD:ALL" entry if it is indeed there.

---

