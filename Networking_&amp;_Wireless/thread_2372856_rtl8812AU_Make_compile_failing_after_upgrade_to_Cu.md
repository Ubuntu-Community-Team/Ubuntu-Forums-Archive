---
title: "rtl8812AU Make compile failing after upgrade to Custom Kernel"
date: 2017-09-29
forum: Networking &amp; Wireless
---

### Post by gunny4you on 2017-09-29
rtl8812AU Make compile is failing after upgrade to Custom Kernel
I have installed 16.0.4 version, after that followed instruction here to install Wireless drivers

```

[COLOR=#111111][FONT=&amp]$ git clone [/FONT][/COLOR]https://github.com/diederikdehaas/rtl8812AU
[COLOR=#111111][FONT=&amp]$ cd [/FONT][/COLOR][COLOR=#111111][FONT=&amp]rtl8812AU[/FONT][/COLOR][COLOR=#111111][FONT=&amp]/[/FONT][/COLOR]
[COLOR=#111111][FONT=&amp]$ make[/FONT][/COLOR]
[COLOR=#111111][FONT=&amp]$ sudo make install[/FONT][/COLOR]
[COLOR=#111111][FONT=&amp]$ sudo modprobe 8812au
[/FONT][/COLOR]
```

Till this point it was successful and wireless worked fine

Now I have installed eve-ng on top of Ubuntu after that I am unable to install back the drivers
Eve-ng installed a custom kernel

[http://www.eve-ng.net/index.php/documentation/installation/bare-install](http://www.eve-ng.net/index.php/documentation/installation/bare-install)

```

 root@eve-ng:/home/gunny/rtl8812AU# uname -r
4.9.40-eve-ng-ukms-2+

```

Getting below error when I am trying to compile it

```

root@eve-ng:/home/gunny/rtl8812AU# make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.9.40-eve-ng-ukms-2+/build M=/home/gunny/rtl8812AU  modules
make[1]: *** /lib/modules/4.9.40-eve-ng-ukms-2+/build: No such file or directory.  Stop.
Makefile:1576: recipe for target 'modules' failed
make: *** [modules] Error 2

```

---

### Post by gunny4you on 2017-09-29
My Wireless Info Script 
[https://pastebin.com/uEPAqLgE](https://pastebin.com/uEPAqLgE)

---

### Post by gunny4you on 2017-09-29
Below is the logs when I connect WIFI Adapter. It says the drivers are installed but getting below error

[ 1735.471978] usb 1-1: new high-speed USB device number 5 using ehci-pci
[ 1735.811140] usb 1-1: New USB device found, idVendor=0bda, idProduct=0811
[ 1735.811146] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1735.811149] usb 1-1: Product: 802.11ac WLAN Adapter 
[ 1735.811152] usb 1-1: Manufacturer: Realtek 
[ 1735.811154] usb 1-1: SerialNumber: 00e04c000001
[ 1736.870963] 8812au: version magic '4.4.0-96-generic SMP mod_unload modversions ' should be '4.9.40-eve-ng-ukms-2+ SMP mod_unload '
[ 1736.875494] rtl8812au: version magic '4.9.40-eve-ng-ukms+ SMP mod_unload ' should be '4.9.40-eve-ng-ukms-2+ SMP mod_unload '

---

### Post by gunny4you on 2017-09-30
I managed to fix this, somehow I managed to change vermagic string in drive .ko file
But not sure how I changed

Can someone tell how this can be exactly changed. Basically I want to understand how to change string in .ko file

Change 
```

root@eve-ng:~/rtl8812AU# modinfo 8812au.ko -F vermagic
4.9.40-eve-ng-ukms+ SMP mod_unload 

```
 
to 

```

 root@eve-ng:/lib/modules/4.9.40-eve-ng-ukms-2+/kernel/drivers/net/wireless# modinfo 8812au.ko -F vermagic
4.9.40-eve-ng-ukms-2+ SMP mod_unload 

```

---

### Post by gunny4you on 2017-09-30
Edited the file with Hexedit and change the vermagic to match the kernel version
Issue is now fixed :)

---

