---
title: "[SOLVED] noob reinstalling ipw2200 wifi not detected, having problems + brain damage"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by toasty mofo on 2008-07-02
Hey, I'm really new to linux in general. I thought I was picking it up pretty good, then my box crashed and killed my wifi.

I want to try reinstalling the ipw2200 driver, but I can't seem to do this. I'm running hardy on an acer travelmate 4100 laptop. I've been trying to reinstall, but it doesn't want to find my ieee80211 files, even after "make IEEE80211_INC=thepathhere", so I guess I need to uninstall all that first.

here's some code
```
dimitri@dimitri-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

My wifi card used to be mapped to eth1.
```
dimitri@dimitri-laptop:~$ lspci
......
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
......
```

This happens whenever I try to install the drivers.

```
dimitri@dimitri-laptop:~/Desktop/ipw/ieee80211-1.2.18$ make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.24-19-generic for ieee80211 components...
make -C /lib/modules/2.6.24-19-generic/build M=/home/dimitri/Desktop/ipw/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:17: 
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.o
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING  			page 1


   1              	.file "ieee80211_module.c"
   9              	.Ltext0:

GAS LISTING  			page 2


DEFINED SYMBOLS
                            *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: At top level:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:339: fatal error: opening dependency file /home/dimitri/Desktop/ipw/ieee80211-1.2.18/.ieee80211_module.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/dimitri/Desktop/ipw/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
dimitri@dimitri-laptop:~/Desktop/ipw/ieee80211-1.2.18$ sudo make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.24-19-generic for ieee80211 components...
make -C /lib/modules/2.6.24-19-generic/build M=/home/dimitri/Desktop/ipw/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:17: 
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.o
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/dimitri/Desktop/ipw/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
dimitri@dimitri-laptop:~/Desktop/ipw/ieee80211-1.2.18$ sudo make install
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
make -C /lib/modules/2.6.24-19-generic/build M=/home/dimitri/Desktop/ipw/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:17: 
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.o
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/dimitri/Desktop/ipw/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
dimitri@dimitri-laptop:~/Desktop/ipw/ieee80211-1.2.18$ cd ipw*
dimitri@dimitri-laptop:~/Desktop/ipw/ieee80211-1.2.18/ipw2200-1.2.2$ sudo make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.24-19-generic/include'.

-e You need to install the ieee80211 subsystem from http://ieee80211.sf.net
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1
dimitri@dimitri-laptop:~/Desktop/ipw/ieee80211-1.2.18/ipw2200-1.2.2$ 

```

I'm sure it's something stupid and simple, but right now I feel like throwing something dangerous and heavy at someone innocent.

Won't you help save the innocents??

---

### Post by toasty mofo on 2008-07-02
bump?

---

### Post by prshah on 2008-07-02
> **toasty mofo said:**
> 

[CODE]dimitri@dimitri-laptop:~/Desktop/ipw/ieee80211-1.2.18$ make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
[color=red]Makefile:20: 'make SHELL=/bin/bash'.[/color]
Makefile:21: 



Did you try this solution?

---

### Post by toasty mofo on 2008-07-03
yup

```

dimitri@dimitri-laptop:~/Desktop/ipw/ieee80211-1.2.18$ make SHELL=/bin/bash
Checking in /lib/modules/2.6.24-19-generic for ieee80211 components...
make -C /lib/modules/2.6.24-19-generic/build M=/home/dimitri/Desktop/ipw/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.o
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c: At top level:
/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.c:339: fatal error: opening dependency file /home/dimitri/Desktop/ipw/ieee80211-1.2.18/.ieee80211_module.o.d: Permission denied
compilation terminated.
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING  			page 1


   1              	.file "ieee80211_module.c"
   9              	.Ltext0:

GAS LISTING  			page 2


DEFINED SYMBOLS
                            *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/home/dimitri/Desktop/ipw/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/dimitri/Desktop/ipw/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
```

also, does this help?

```
dimitri@dimitri-laptop:~/Desktop/ipw/ieee80211-1.2.18$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32 maxlatency=24 mingnt=3
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:7c:cb:47
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.5 latency=32 module=ssb multicast=yes
```

---

### Post by chili555 on 2008-07-03
What about the native ipw2200 driver did not work for you? Have you already remove it or the native ieee80211 suite? Does your card come to life with:```
sudo modprobe ipw2200
```I notice the tar.gz you are trying to install is about a year old and so I really wonder if it's altogether compatible with 2.6.24-x kernels.

---

### Post by toasty mofo on 2008-07-03
```
dimitri@dimitri-laptop:~$ sudo modprobe ipw2200
[sudo] password for dimitri: 
WARNING: Could not open '/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211.ko': No such file or directory
FATAL: Error inserting ipw2200 (/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

What really confuses me is that I can see those files in that directory :S

The native ipw2200 worked fine, it just disappeared during a bad crash (computer froze, had to hard reset). How would I go about replacing that?

---

### Post by chili555 on 2008-07-03
Well, first, let's see wht dmesg has to say as suggested. Please post ```
dmesg | grep ipw
dmesg | grep ieee80211
```Thanks.> it just disappeared during a bad crashOops! That'll sometimes do it.

---

### Post by toasty mofo on 2008-07-03
```
dimitri@dimitri-laptop:~$ dmesg | grep ipw
[   33.708535] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   33.708689] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   33.708741] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   33.708918] ipw2200: Unknown symbol ieee80211_txb_free
[   33.708999] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   33.709180] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   33.709234] ipw2200: Unknown symbol escape_essid
[   33.709356] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   33.709643] ipw2200: Unknown symbol ieee80211_set_geo
[   33.709821] ipw2200: Unknown symbol ieee80211_rx
[   33.709972] ipw2200: Unknown symbol ieee80211_channel_to_index
[   33.710287] ipw2200: Unknown symbol ieee80211_rx_mgt
[   33.710338] ipw2200: Unknown symbol ieee80211_get_geo
[   33.710428] ipw2200: Unknown symbol free_ieee80211
[   33.710670] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   33.710789] ipw2200: Unknown symbol alloc_ieee80211
[  175.040326] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[  175.040648] ipw2200: Unknown symbol ieee80211_wx_set_encode
[  175.040763] ipw2200: Unknown symbol ieee80211_wx_get_encode
[  175.041128] ipw2200: Unknown symbol ieee80211_txb_free
[  175.041301] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[  175.041674] ipw2200: Unknown symbol ieee80211_wx_get_scan
[  175.041783] ipw2200: Unknown symbol escape_essid
[  175.042057] ipw2200: Unknown symbol ieee80211_freq_to_channel
[  175.042641] ipw2200: Unknown symbol ieee80211_set_geo
[  175.043008] ipw2200: Unknown symbol ieee80211_rx
[  175.043303] ipw2200: Unknown symbol ieee80211_channel_to_index
[  175.043943] ipw2200: Unknown symbol ieee80211_rx_mgt
[  175.044057] ipw2200: Unknown symbol ieee80211_get_geo
[  175.044247] ipw2200: Unknown symbol free_ieee80211
[  175.044741] ipw2200: Unknown symbol ieee80211_is_valid_channel
[  175.044990] ipw2200: Unknown symbol alloc_ieee80211
dimitri@dimitri-laptop:~$ dmesg | grep ieee80211
[   33.708535] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   33.708689] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   33.708741] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   33.708918] ipw2200: Unknown symbol ieee80211_txb_free
[   33.708999] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   33.709180] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   33.709356] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   33.709643] ipw2200: Unknown symbol ieee80211_set_geo
[   33.709821] ipw2200: Unknown symbol ieee80211_rx
[   33.709972] ipw2200: Unknown symbol ieee80211_channel_to_index
[   33.710287] ipw2200: Unknown symbol ieee80211_rx_mgt
[   33.710338] ipw2200: Unknown symbol ieee80211_get_geo
[   33.710428] ipw2200: Unknown symbol free_ieee80211
[   33.710670] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   33.710789] ipw2200: Unknown symbol alloc_ieee80211
[  175.040326] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[  175.040648] ipw2200: Unknown symbol ieee80211_wx_set_encode
[  175.040763] ipw2200: Unknown symbol ieee80211_wx_get_encode
[  175.041128] ipw2200: Unknown symbol ieee80211_txb_free
[  175.041301] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[  175.041674] ipw2200: Unknown symbol ieee80211_wx_get_scan
[  175.042057] ipw2200: Unknown symbol ieee80211_freq_to_channel
[  175.042641] ipw2200: Unknown symbol ieee80211_set_geo
[  175.043008] ipw2200: Unknown symbol ieee80211_rx
[  175.043303] ipw2200: Unknown symbol ieee80211_channel_to_index
[  175.043943] ipw2200: Unknown symbol ieee80211_rx_mgt
[  175.044057] ipw2200: Unknown symbol ieee80211_get_geo
[  175.044247] ipw2200: Unknown symbol free_ieee80211
[  175.044741] ipw2200: Unknown symbol ieee80211_is_valid_channel
[  175.044990] ipw2200: Unknown symbol alloc_ieee80211
dimitri@dimitri-laptop:~$ 

```

gory!

---

### Post by chili555 on 2008-07-03
> gory!Yes, indeed! Can you interrupt the boot process at the GRUB prompt and boot into an earlier kernel, 2.6.24-18 or -17, perhaps and does the native *ipw2200* load and connect? If so, we might be able to cheat this a little.

---

### Post by toasty mofo on 2008-07-03
I only have the hardy live cd, which I used to install in a partition. Could you recommend something?

Thanks for your help so far.

---

### Post by chili555 on 2008-07-03
Perhaps I did not explain myself well enough. Turn off your computer. Press the power button to start it. A very quick message will appear from the computer manufacturer asking you to press F1 or delete or similar to enter the BIOS or Set-up pages. Then the word 'GRUB' will appear and a 3-second countdown. Press Esc and a menu will appear that lists all the kernels on your machine. Arrow down to any other than the highest listing, such as 2.6.24-18, and press b for boot. Do not pick 'recovery mode.' Let the computer boot into a previous kernel and now try your wireless device. Does it work? If so, we can repair -19.

---

### Post by toasty mofo on 2008-07-05
Wow, I cant believe I didn't notice that. Yeah, I loaded a previous version and the wireless works fine on that.

---

### Post by chili555 on 2008-07-05
All right! That means that ipw2200 or ieee80211 or both are somehow corrupted in the kernel image for 2.6.24-19, but working fine in -18. While you are booted in to -18, go to System-Administration-Synaptic and serach for *linux-image-2.6.24-19-generic*, right-click it and 'Mark for reinstallation.' Click 'Apply' and let it whirl and buzz. Reboot into your -19 kernel and see if wireless now works.

---

### Post by toasty mofo on 2008-07-05
Wahey! Such a simple solution, I'm totally humbled. Thanks so much for your help.

On a side note, do you have any idea what could have caused this? Is it one of those occasional problems or a fluke screw-up?

Thanks man.

---

### Post by chili555 on 2008-07-05
> a fluke screw-upNo electro-mechanical device is perfect, although computers may be 99.999%, the are not 100% perfect.

It's handy knowing you have an earlier kernel or two on hand, just in case of a problem, either man-made or metaphysical. It's a life-jacket.

Try to match that, Windows.

---

