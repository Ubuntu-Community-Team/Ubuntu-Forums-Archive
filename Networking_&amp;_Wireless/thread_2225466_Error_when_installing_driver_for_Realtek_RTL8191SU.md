---
title: "Error when installing driver for Realtek RTL8191SU wifi dongle"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by nitish2 on 2014-05-21
I have been trying to install the linux drivers for my wifi dongle which works perfectly in Windows but have failed to install on several variants of Debian based Linux.

I have tried both the latest version of the [driver ]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true")(RTL819xSU_usb_linux_v2.6.6.0.20120405) and a previous version (RTL8188SU_usb_linux_v2.6.0006.20100625) which people reported on forums as having installed successfully.

In each two errors were reported. Below is the output for my latest attempt on Ubuntu 14.04 64-bit:

[SIZE=1][FONT=arial][SIZE=2]Note that /tmp/folder is actually /tmp/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625. I replaced the text for better legibility.[/SIZE][/FONT]

userx@ubuntu:/tmp/folder$ ls
autoconf_rtl8712_usb_linux.h  eeprom       ioctl     os_intf  wlan0dhcp
clean                         efuse        led       pwrctrl  wpa1.conf
cmd                           hal          Makefile  recv     xmit
config                        ifcfg-wlan0  mlme      rf
crypto                        include      mp        runwpa
debug                         io           os_dep    sta_mgt
userx@ubuntu:/tmp/folder$ sudo su
[sudo] password for userx: 
root@ubuntu:/tmp/folder# make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-24-generic/build M=/tmp/folder  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /tmp/folder/cmd/rtl871x_cmd.o
In file included from /tmp/folder/cmd/rtl871x_cmd.c:21:0:
/tmp/folder/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/tmp/folder/include/osdep_service.h:133:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  ptimer->data = (u32)cntx;
                 ^
In file included from /tmp/folder/cmd/rtl871x_cmd.c:21:0:
/tmp/folder/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/tmp/folder/include/osdep_service.h:359:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
  daemonize("%s", "RTKTHREAD");
  ^
In file included from /tmp/folder/include/rtl871x_ht.h:7:0,
                 from /tmp/folder/include/drv_types.h:48,
                 from /tmp/folder/cmd/rtl871x_cmd.c:22:
/tmp/folder/include/wifi.h: In function &#8216;get_da&#8217;:
/tmp/folder/include/wifi.h:305:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                                              ^
/tmp/folder/include/wifi.h:331:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:305:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                            ^
/tmp/folder/include/wifi.h:331:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:305:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                                              ^
/tmp/folder/include/wifi.h:334:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:305:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                            ^
/tmp/folder/include/wifi.h:334:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:309:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/tmp/folder/include/wifi.h:337:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:309:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/tmp/folder/include/wifi.h:337:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:309:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/tmp/folder/include/wifi.h:340:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:309:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/tmp/folder/include/wifi.h:340:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/tmp/folder/include/wifi.h: In function &#8216;get_sa&#8217;:
/tmp/folder/include/wifi.h:307:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                                              ^
/tmp/folder/include/wifi.h:355:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:307:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                            ^
/tmp/folder/include/wifi.h:355:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:309:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/tmp/folder/include/wifi.h:358:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:309:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/tmp/folder/include/wifi.h:358:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:307:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                                              ^
/tmp/folder/include/wifi.h:361:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:307:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                            ^
/tmp/folder/include/wifi.h:361:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:311:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr4Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 24))
                                              ^
/tmp/folder/include/wifi.h:364:9: note: in expansion of macro &#8216;GetAddr4Ptr&#8217;
    sa = GetAddr4Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:311:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr4Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 24))
                            ^
/tmp/folder/include/wifi.h:364:9: note: in expansion of macro &#8216;GetAddr4Ptr&#8217;
    sa = GetAddr4Ptr(pframe);
         ^
/tmp/folder/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/tmp/folder/include/wifi.h:309:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/tmp/folder/include/wifi.h:378:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:309:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/tmp/folder/include/wifi.h:378:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:307:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                                              ^
/tmp/folder/include/wifi.h:381:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:307:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                            ^
/tmp/folder/include/wifi.h:381:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:305:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                                              ^
/tmp/folder/include/wifi.h:384:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    sa = GetAddr1Ptr(pframe);
         ^
/tmp/folder/include/wifi.h:305:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                            ^
/tmp/folder/include/wifi.h:384:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    sa = GetAddr1Ptr(pframe);
         ^
In file included from /tmp/folder/include/drv_types.h:51:0,
                 from /tmp/folder/cmd/rtl871x_cmd.c:22:
/tmp/folder/include/rtl871x_cmd.h: At top level:
/tmp/folder/include/rtl871x_cmd.h:88:25: error: field &#8216;event_tasklet&#8217; has incomplete type
   struct tasklet_struct event_tasklet;
                         ^
In file included from /tmp/folder/include/drv_types.h:53:0,
                 from /tmp/folder/cmd/rtl871x_cmd.c:22:
/tmp/folder/include/rtl871x_xmit.h:336:24: error: field &#8216;xmit_tasklet&#8217; has incomplete type
  struct tasklet_struct xmit_tasklet;
                        ^
In file included from /tmp/folder/include/drv_types.h:54:0,
                 from /tmp/folder/cmd/rtl871x_cmd.c:22:
/tmp/folder/include/rtl871x_recv.h:185:24: error: field &#8216;recv_tasklet&#8217; has incomplete type
  struct tasklet_struct recv_tasklet;
                        ^
In file included from /tmp/folder/include/drv_types.h:54:0,
                 from /tmp/folder/cmd/rtl871x_cmd.c:22:
/tmp/folder/include/rtl871x_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/tmp/folder/include/rtl871x_recv.h:415:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  return (union recv_frame*)(((uint)rxmem>>RXFRAME_ALIGN) <<RXFRAME_ALIGN) ;
                              ^
/tmp/folder/include/rtl871x_recv.h:415:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  return (union recv_frame*)(((uint)rxmem>>RXFRAME_ALIGN) <<RXFRAME_ALIGN) ;
         ^
In file included from /tmp/folder/include/drv_types.h:58:0,
                 from /tmp/folder/cmd/rtl871x_cmd.c:22:
/tmp/folder/include/rtl871x_io.h: At top level:
/tmp/folder/include/rtl871x_io.h:17:28: fatal error: linux/smp_lock.h: No such file or directory
 #include <linux/smp_lock.h>
                            ^
cc1: some warnings being treated as errors
compilation terminated.
make[2]: *** [/tmp/folder/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/tmp/folder] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [modules] Error 2
root@ubuntu:/tmp/folder# 
[/SIZE]

Note that I have followed the steps from post: [http://ubuntuforums.org/showthread.php?t=1674994](http://ubuntuforums.org/showthread.php?t=1674994)

---

