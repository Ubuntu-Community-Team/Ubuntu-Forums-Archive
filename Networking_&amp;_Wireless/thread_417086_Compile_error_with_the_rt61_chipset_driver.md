---
title: "Compile error with the rt61 chipset driver"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by NickL87 on 2007-04-21
Hi all

I have just installed Ubuntu 7.04, but i have some problems getting my wireless network up and running. I am using this guide: [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980), which i have used in older versions of Ubuntu. This time when i try to install it I, however, get an error when i am  activate the ”make all” command. I have tried installing the Linux headers, and the gcc-3.4 build-essential
 without luck.

The error i keep getting:

```

/Module$ sudo make all
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/nick/Desktop/Dokumenter/Install/Drivers/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Går til katalog '/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/nick/Desktop/Dokumenter/Install/Drivers/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/nick/Desktop/Dokumenter/Install/Drivers/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/nick/Desktop/Dokumenter/Install/Drivers/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: fejl: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/nick/Desktop/Dokumenter/Install/Drivers/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/home/nick/Desktop/Dokumenter/Install/Drivers/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: advarsel: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/nick/Desktop/Dokumenter/Install/Drivers/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Fejl 1
make[1]: *** [_module_/home/nick/Desktop/Dokumenter/Install/Drivers/RT61_Linux_STA_Drv1.1.0.0/Module] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Fejl 2

```

Fejl = error

Nickl87

---

### Post by NickL87 on 2007-04-21
Are there really no one who knows the solution to this problem? :confused:

---

### Post by threeten on 2007-04-21
I had the exact same problem.  Go here

[http://218.46.125.189/wicd/wb/](http://218.46.125.189/wicd/wb/)

and install Wicd.  Everything just works.

---

### Post by jogege on 2007-04-22
My RT61 based card works without any problem in Feisty. It seems Feisty comes with the RT61 module rather than the RT61pci module so I dont think you need to do anything to make it work. Only issue I have is that DHCP and network manager  does not work, but feisty's networking and setting IP address works.

---

### Post by lukaszJarochowski on 2007-04-22
If you have problems with compiling ralink rt61 driver then try this howto:
[http://ubuntuforums.org/showthread.php?t=415693]("http://ubuntuforums.org/showthread.php?t=415693")

this hould help

---

### Post by NickL87 on 2007-04-22
> **lukaszJarochowski said:**
> If you have problems with compiling ralink rt61 driver then try this howto:
[http://ubuntuforums.org/showthread.php?t=415693]("http://ubuntuforums.org/showthread.php?t=415693")

this hould help

I followed the guide, and I manage to get the driver compiled :) I do however get a lot of warnings, which unfortunately must have some sort of an affect on the result, since I get an error when I write: 

```

sudo modprobe rt61

FATAL: Error inserting rt61 (/lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/rt61.ko): Invalid module format

```

---

### Post by NickL87 on 2007-04-22
> **jogege said:**
> My RT61 based card works without any problem in Feisty. It seems Feisty comes with the RT61 module rather than the RT61pci module so I dont think you need to do anything to make it work. Only issue I have is that DHCP and network manager  does not work, but feisty's networking and setting IP address works.

Okay, I wish I could say the same, but Ubuntu creates no interface for my network card, but it does however look like it associates my card with a driver :S

---

### Post by Barrakketh on 2007-04-25
I have a fix for the problem.  I contacted Ralink and told them the error messages and the workaround.  They replied with a fix:

[quote=Mike Hsieh]Dear Michael:

Please modify the driver for the linux based driver of kernel 2.6.20.
   #if WIRELESS_EXT >= 12
         #if WIRELESS_EXT < 17
         net_dev->get_wireless_stats = RT61_get_wireless_stats;
         #endif
   net_dev->wireless_handlers = (struct iw_handler_def *)&rt61_iw_handler_def; #endif
   #endif

Best Regards,
 Mike Hsieh[/quote]

So, starting on line 196 in rtmp_main.c you'll see the following:

```
#if WIRELESS_EXT >= 12
    net_dev->get_wireless_stats = RT61_get_wireless_stats;
    net_dev->wireless_handlers = (struct iw_handler_def *) &rt61_iw_handler_def;
#endif
```

Change it so it reads:

```
#if WIRELESS_EXT >= 12
	#if WIRELESS_EXT < 17
    		net_dev->get_wireless_stats = RT61_get_wireless_stats;
	#endif

    net_dev->wireless_handlers = (struct iw_handler_def *) &rt61_iw_handler_def;

#endif
```

---

