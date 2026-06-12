---
title: "Edimax EW-7612UAn"
date: 2014-02-22
forum: Networking &amp; Wireless
---

### Post by maieuto on 2014-02-22
Hi,

Trouble finding support for new Edimax EW-7612Uan wifi usb adapter.

Ubuntu recognises it as soon as its plugged in and lists all the nearby SSIDs in Network Manager, however in general it refuses to connect to my BT home hub.

```
$ ifconfig 

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:da:1e:f9  
          inet6 addr: fe80::821f:2ff:feda:1ef9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13899 (13.8 KB)  TX bytes:19065 (19.0 KB)

I tried installing the driver from the hardware manufactures website [http://www.edimax.com/en/support_detail.php?pd_id=356&pl1_id=1&pl2_id=](http://www.edimax.com/en/support_detail.php?pd_id=356&pl1_id=1&pl2_id=)
but get compile errors.
$./configure   
no such file or directory

$ ./config

./config: line 6: CONFIG_RTL8711: command not found
./config: line 7: CONFIG_RTL8712: command not found
./config: line 10: CONFIG_USB_HCI: command not found
./config: line 11: CONFIG_SDIO_HCI: command not found
./config: line 14: CONFIG_MP_INCLUDED: command not found
./config: line 16: CONFIG_PLATFORM_I386_PC: command not found
./config: line 17: CONFIG_PLATFORM_ARM_S3C: command not found
./config: line 18: CONFIG_PLATFORM_ARM_PXA: command not found
./config: line 19: CONFIG_PLATFORM_MIPS_RMI: command not found
./config: line 20: CONFIG_PLATFORM_RTK_DMP: command not found
./config: line 21: CONFIG_PLATFORM_MIPS_PLM: command not found
./config: line 22: CONFIG_PLATFORM_RTD2880B: command not found
./config: line 23: CONFIG_PLATFORM_MSTAR389: command not found
./config: line 25: CONFIG_MLME_EXT: command not found
./config: line 26: CONFIG_DRVEXT_MODULE: command not found

$ make

...

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.11.0-15-generic/build M=/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625  modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  CC [M]  /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.o
In file included from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:21:0:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/osdep_service.h:133:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
In file included from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:21:0:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/osdep_service.h:359:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
In file included from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_ht.h:7:0,
                 from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:48,
                 from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h: In function &#8216;get_da&#8217;:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:331:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:331:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:334:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:334:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:337:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:337:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:340:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:340:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h: In function &#8216;get_sa&#8217;:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:355:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:355:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:358:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:358:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:361:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:361:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:364:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:364:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:378:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:378:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:381:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:381:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:384:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/wifi.h:384:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:51:0,
                 from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_cmd.h: At top level:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_cmd.h:88:25: error: field &#8216;event_tasklet&#8217; has incomplete type
In file included from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:53:0,
                 from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_xmit.h:336:24: error: field &#8216;xmit_tasklet&#8217; has incomplete type
In file included from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:54:0,
                 from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_recv.h:185:24: error: field &#8216;recv_tasklet&#8217; has incomplete type
In file included from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:54:0,
                 from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_recv.h:415:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_recv.h:415:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:58:0,
                 from /home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_io.h: At top level:
/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_io.h:17:28: fatal error: linux/smp_lock.h: No such file or directory
cc1: some warnings being treated as errors
compilation terminated.
make[2]: *** [/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/lorax/Downloads/7612_22_Linux_Driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make: *** [modules] Error 2
```

---

### Post by wildmanne39 on 2014-02-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2014-02-22
That driver was made in 2010 so I doubt that it will compile on the newer versions of ubuntu.

I am going to post a script for your to run so other people will have the information needed to help you at the moment I am way under the weather and am not up to it.

Copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by maieuto on 2014-03-15
Wireless-info.txt attached

---

