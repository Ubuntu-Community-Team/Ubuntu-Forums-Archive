---
title: "New Wireless Adapter"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2017-04-16
My desktop keyboard top came off my desk and busted my wifi adapter.  I bought an ASUS USB-AC51 Wireless Adapter and the Linux instructions say to

```
MT7610U Linux Driver quick start        
 
==================== 
Check tools:   

==================== 
*Before install driver, please check already install compile tool and  kernel source code 
 
1>Install compile tool 
    $yum install gcc-c++ 
 
2>check kernel source code exists /usr/src/kernels/ "kernel name" 
 
    Download your kernel source code 
    *http://www.kernel.org/pub/linux/kernel/          
    or 
    $yum install kernel-devel 
 
 
 
==================== 
Build Instructions:   

==================== 
1> $tar -xvf mt7610u_wifi_sta_vxxxx_dpo_xxxxxxxx.tar.bz2 
     go to "mt7610u_wifi_sta_vxxxx_dpo_xxxxxxxx" directory. 
     
 

2> In Makefile
      
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
      
     define the linux kernel source include file path LINUX_SRC
      
     modify to meet your need.
 
 
3> In os/linux/config.mk 
     
     define the GCC and LD of the target machine
     
     define the compiler flags CFLAGS
     
     modify to meet your need. 
     ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
        
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
               
         => $wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d 
     ** Build for being controlled by WpaSupplicant with Ralink Driver
        
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
        
         => $wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d 
 
4> $make            
     
     # compile driver source code, need administrator.
     
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      
        => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c 
 
5> $make install 
     #install driver 
     #copy RT2870STA.dat to /etc/Wireless/RT2870STA/RT2870STA.dat 
 
6>$vi /etc/rc.d/rc.local 
     #input "ifconfig ra0 up" 
 
     ** Ubuntu 13.04 don't have this file. 
    $reboot 
 
7> unload driver    
     
     $ifconfig ra0 down 

     $make uninstall 
     $reboot
```

My question is how do I do this if I have no internet connection on my desktop?  :confused:

---

### Post by Bucky Ball on 2017-04-16
The irony is you need an ethernet cable to get some wifi adapters working. Have you plugged it in an checked if it is picked up? The driver may already be in the kernel.

If you haven't already, plug it in (without an ethernet cable or any other wireless card in), wait a bit and see what happens. You might try a reboot (with the stick in).

If nothing, give the output of the following when the stick is in.

```
lsusb
```

... and immediately after you've plugged the USB in run ...

```
dmesg
```

Post the end of that message concerning the wifi.

(PS: Just looking through your post, looks like that might use the STA driver. You will find that in 'Additional Drivers' probably, but you will need to update while you are online to get it. There may be a way of doing an offline install of that driver, but let's see what happens once you've done the above.)

---

### Post by shane_faulkinbury2 on 2017-04-16
Okay, here's the screen shot.  Apparently "lsub" isn't installed.  :(  If you need anything further down on the "dmesg" command I'll provide it, but it's pretty long.

---

### Post by chili555 on 2017-04-16
> Apparently "lsub" isn't installed.He requested:```
lsusb
```If this is truly an mt7610u device, we have a long, rocky road ahead of us; probably a dead-end.

---

### Post by shane_faulkinbury2 on 2017-04-16
Well I can drag it down stairs and use some ethernet to hook it up to the router if need be, but I'll have to do it after some Easter stuff seeing as this is Easter!   :)

Okay I'm ready to drag the thing downstairs, but I can't leave it down there longer than tonight so I'd like to get this done.  I'll give it a go on my own with the ethernet cable, but we shall see!  :rolleyes::rolleyes::rolleyes:

---

### Post by chili555 on 2017-04-16
Please run and post:```
lsusb
```

---

### Post by shane_faulkinbury2 on 2017-04-16
As it turn out since I'm on a wireless network I couldn't find an ethernet cord.  I called both Best Buy and Fryes, but both were closed due to Easter.  So I'll take this up tomorrow.

---

### Post by chili555 on 2017-04-17
With the greatest respect, nobody suggests that you get an ethernet cord, drag the computer downstairs and get started. Frankly, I suspect that all the needed tools to compile a driver, if one existed that would work, are already present on your install.

I had hoped that by providing the device usb.id from the command:```
lsusb
```...that then I could show you that the included driver is far too old to compile on any recent Ubuntu version. I could then point you to a sort-of almost working driver that I have experience with. You could download it on some other computer and transfer it on a USB drive. After compiling it, you could post back and tell me that it's terrible.

Finally, after 25-30 fruitless posts, I could suggest that you instead spend your Best Buy and Fryes time and money getting a different, fully supported device.> 2>check kernel source code exists /usr/src/kernels/ "kernel name" 
 
    Download your kernel source code 
    *[http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/)          
    or 
    $yum install kernel-devel 
 With little respect to MediaTek, almost no-one is ever going to get this thing to compile by downloading the kernel source at kernel.org. Did they provide you a driver file? Yes! Of course! Is it a driver that you can likely compile and use? Uhh, no.

---

### Post by shane_faulkinbury2 on 2017-04-17
Okay, I'm on ethernet and I'm stuck at the yum part.  Yum is installed and also  yum-config-manager.  I do not see where to change the repo in  yum-config-manager to install the yum install gcc-c++.

---

### Post by chili555 on 2017-04-17
> **shane_faulkinbury2 said:**
> Okay, I'm on ethernet and I'm stuck at the yum part.  Yum is installed and also  yum-config-manager.  I do not see where to change the repo in  yum-config-manager to install the yum install gcc-c++.Yes, indeed. As long as you persist in trying to follow instructions that are not for Ubuntu and not for any current kernel version, I am sure you will get stuck.

Please read carefully my just previous post. I especially draw your attention to:> Frankly, I suspect that all the needed tools to compile a driver, if one existed that would work, are already present on your install.

---

### Post by Bucky Ball on 2017-04-17
Yum? Nothing to do with Ubuntu. Read carefully and follow chili555. They are one of the best for wifi that we are lucky to have around here and you should take full advantage of their help. :)

---

