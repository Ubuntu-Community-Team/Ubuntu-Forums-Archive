---
title: "DRiver loading for Edimax - help for a noob"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by rob42 on 2009-01-27
Hello All
I am new to Linux and am on a step learning curve. My lastest wall is loading the drivers for a edimax  ew-7318usg adapter.
The supplied cd comes with linux drivers but even though I have tried to follow some posts found here it hasn't worked.
I also have downloaded and used wine -  this works in part - but the utilies program can't see the adapter ( the adapter does work as loaded it onto windows machine -worked very well - also the unit flashes as you plug it to the laptops usb port)

Would some be prepared to go step by with me ? 
Many thanks

Rob

---

### Post by rob42 on 2009-01-28
ok i have run    lshw -C network   

 *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:24:0d:e2
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:52:94:94
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=10.70.20.45 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:3a:03:c2:fb:22
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:1f:1f:35:07:8b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
orac@orac:~$ 

is what I get - this shows (to my eyes any way ) the intel wireless adapter which I have not been able to get to work ,plus the usb unit ( wlan1 ) as the serial number and mac address on unit are the same.

I have tried to follow some instructons supplied by ralink , but am not able to download the driver (can not connect is the message ) also these are for 8.04 ( if that makes any difference)
am sure the nswer is simple but at the mo I am pulling whats left of my hair out :D

Rob

---

### Post by rob42 on 2009-01-28
ok just to keep you updated have got this far
>  orac@orac:~/Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$ sudo make
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/orac/Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/orac/Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.o
/home/orac/Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.c: In function ‘usb_rtusb_close_device’:
/home/orac/Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.c:443: error: implicit declaration of function ‘kill_proc’
make[2]: *** [/home/orac/Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/orac/Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2
orac@orac:~/Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$   

any guides out there :(

---

### Post by rob42 on 2009-01-28
Is there anyone that can give me a pointer or two??

---

