---
title: "Installing Drivers for Edimax EW7811UN 150Mbp USB Adapter Ubuntu 13.04 64 bit"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by chiques on 2013-09-20
Hello Community,
I just purchased this USB Wifi Adapter for my laptop (the internal one died) because of it's size mostly. Unfortunately their documentation makes no sense and looks like it written back in the 90's (see readmen.txt attached). What little does make sense to me compiles with errors.

Check it out here [http://www.edimax.com/en/produce_detail.php?pd_id=347&pl1_id=1]("http://www.edimax.com/en/produce_detail.php?pd_id=347&pl1_id=1")

Here is what I'm running:
> 
chiques@ubuntu-oldfaithful:~$ lsb_release -d
Description:	Ubuntu 13.04
chiques@ubuntu-oldfaithful:~$ uname -mr
3.8.0-19-generic x86_64
chiques@ubuntu-oldfaithful:~$ lsusb
Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
chiques@ubuntu-oldfaithful:~$ lsmod | egrep 'rt2|rt3'
chiques@ubuntu-oldfaithful:~$ 


By default Ubuntu does detect the adapter and I have my wireless access point as an option from the icon. Problem is it never connects (times out). In slide 5 of the presentation, it asks to simply run 'make'

When I run make I get this junk
```

rtl8192CU_linux_v2.0.939.20100726$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-19-generic/build M=/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.o
In file included from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:21:0:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h: In function ‘_init_timer’:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h:146:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
In file included from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:21:0:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h: In function ‘thread_enter’:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/osdep_service.h:381:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
In file included from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_ht.h:7:0,
                 from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:55,
                 from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function ‘get_da’:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:331:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:334:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:337:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:340:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function ‘get_sa’:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:355:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:358:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:361:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:364:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h: In function ‘get_hdr_bssid’:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:378:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:381:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/wifi.h:384:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:60:0,
                 from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_xmit.h: At top level:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_xmit.h:318:24: error: field ‘xmit_tasklet’ has incomplete type
In file included from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:61:0,
                 from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:189:24: error: field ‘recv_tasklet’ has incomplete type
In file included from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:61:0,
                 from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:410:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:66:0,
                 from /home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_io.h: At top level:
/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/include/rtw_io.h:17:28: fatal error: linux/smp_lock.h: No such file or directory
cc1: some warnings being treated as errors
compilation terminated.
make[2]: *** [/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/chiques/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Error 2
chiques@ubuntu-oldfaithful:~/Downloads/rtl8192CU_8188CU_linux_v2.0.939.20100726/driver/rtl8192CU_linux_v2.0.939.20100726$ 


```



I'm not sure how to read this but I see alot of the word "errors" and I also don't see the file to run 
> insmod 8192cu.ko

Any help or guidance is greatly appreciated.

---

### Post by chiques on 2013-09-21
This is the fix.
[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/]("https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/")

*IMPORTANT*
You must do the black listing and module loading described by *(the install.sh didn't make sense since it doesn't exist int he download)*:

[http://ubuntuforums.org/showthread.php?t=2092934&p=12395780#post12395780](http://ubuntuforums.org/showthread.php?t=2092934&p=12395780#post12395780)

"
> add the name of the new module (e.g. "8192cu") to the end of the file /etc/modules so the module will load automatically at each reboot.
"
[http://ubuntuforums.org/showthread.php?t=2092934&p=12396057#post12396057]("http://ubuntuforums.org/showthread.php?t=2092934&p=12396057#post12396057")

Also,
Edimax support was good, they referred me to the post. Thanks Judy!

---

### Post by kingmidget on 2014-04-04
Do you know where I might find the version of this: 

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

For 12.04?

---

