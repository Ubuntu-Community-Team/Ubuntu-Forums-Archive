---
title: "Installing r8712u module for DWA-130 E1 Wireless Adapter"
date: 2016-03-23
forum: Networking &amp; Wireless
---

### Post by petros5 on 2016-03-23
So just a heads up, my knowledge when it comes to Linux is very limited. I'm on **Ubuntu 14.04 LTS**.

I'm using a Wireless N300 USB Adapter,** DWA-130 E1**.

When entering the command **iwconfig wlan0**, I can see **Mod:Managed**. I want to change this to** monitor**.

I enter:
**sudo ifconfig wlan0 down**
**sudo iwconfig wlan0 mode monitor**[B]
sudo iwconfig wlan0[/B]

After the second command, I get:
[B]Error for wireless request "Set Mode" (8B06) :
  SET failed on device wlan0 ; Invalid argument.[/B]

From what I've gathered, I believe to be missing a driver for this to work. Correct me if I'm wrong. I also believe the driver that I require to be the **r8712u module**. Again, correct me if I'm wrong.

I'd basically require help to install this module (assuming that this is what I actually do need to do).

I've found the following package, which I believe contains this module: **rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405**

I'm not too sure on how to proceed from here. If I try to run
[B]sudo ./install.sh > ../out.txt 2> ../err.txt
[/B]
I get a bunch of error messages, which I'm copy pasting below.

```
In file included from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:23:0:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h:151:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  ptimer->data = (u32)cntx;
                 ^
In file included from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:23:0:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h:393:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
  daemonize("%s", "RTKTHREAD");
  ^
In file included from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ht.h:25:0,
                 from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:67,
                 from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h: In function &#8216;get_da&#8217;:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:324:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:350:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:324:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:350:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:324:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:353:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:324:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:353:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:328:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:356:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:328:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:356:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:328:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:359:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:328:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:359:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h: In function &#8216;get_sa&#8217;:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:326:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:374:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:326:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:374:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:328:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:377:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:328:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:377:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:326:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:380:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:326:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:380:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:330:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr4Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 24))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:383:9: note: in expansion of macro &#8216;GetAddr4Ptr&#8217;
    sa = GetAddr4Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:330:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr4Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 24))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:383:9: note: in expansion of macro &#8216;GetAddr4Ptr&#8217;
    sa = GetAddr4Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:328:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:397:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:328:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:397:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:326:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:400:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:326:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:400:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:324:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:403:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    sa = GetAddr1Ptr(pframe);
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:324:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h:403:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    sa = GetAddr1Ptr(pframe);
         ^
In file included from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:70:0,
                 from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h: At top level:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h:107:25: error: field &#8216;event_tasklet&#8217; has incomplete type
   struct tasklet_struct event_tasklet;
                         ^
In file included from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:72:0,
                 from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_xmit.h:355:24: error: field &#8216;xmit_tasklet&#8217; has incomplete type
  struct tasklet_struct xmit_tasklet;
                        ^
In file included from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:73:0,
                 from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:205:24: error: field &#8216;recv_tasklet&#8217; has incomplete type
  struct tasklet_struct recv_tasklet;
                        ^
In file included from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h:73:0,
                 from /home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:24:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:435:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  return (union recv_frame*)(((uint)rxmem>>RXFRAME_ALIGN) <<RXFRAME_ALIGN) ;
                              ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h:435:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  return (union recv_frame*)(((uint)rxmem>>RXFRAME_ALIGN) <<RXFRAME_ALIGN) ;
         ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c: In function &#8216;_init_cmd_priv&#8217;:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:93:75: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  pcmdpriv->cmd_buf = pcmdpriv->cmd_allocated_buf  +  CMDBUFF_ALIGN_SZ - ( (uint)(pcmdpriv->cmd_allocated_buf) & (CMDBUFF_ALIGN_SZ-1));
                                                                           ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:101:60: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  pcmdpriv->rsp_buf = pcmdpriv->rsp_allocated_buf  +  4 - ( (uint)(pcmdpriv->rsp_allocated_buf) & 3);
                                                            ^
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c: In function &#8216;_init_evt_priv&#8217;:
/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c:135:59: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  pevtpriv->evt_buf = pevtpriv->evt_allocated_buf  +  4 - ((unsigned int)(pevtpriv->evt_allocated_buf) & 3);
                                                           ^
cc1: some warnings being treated as errors
make[2]: *** [/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/petros/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make: *** [modules] Error 2
```

Anyway I can get this working?

---

### Post by chili555 on 2016-03-23
Don't you already have a driver for your device?```
lsmod
```Does your device and driver combination support monitor mode?```
iw list
```Here is a sample from my machine:```
Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * [COLOR="#FF0000"]monitor[/COLOR]
		 * P2P-client
		 * P2P-GO
		 * P2P-device

```>  rtl8712_8188_8191_8192SU_usb_linux_v[COLOR="#FF0000"]2.6.6[/COLOR].0.201204 05
That signifies that the driver was written for kernel version 2.6.6 and a few steps later. Which version are you running?```
uname -r
```We really can't put wooden wheels on our sleek, black BMWs.

It is doubtful that you will solve any issue by installing an older, in fact, older than dirt, driver.

Please see: [https://wikidevi.com/wiki/R8712u#Supported_modes](https://wikidevi.com/wiki/R8712u#Supported_modes)> Supported modes

    STA (Station) mode: supported
    IBSS (Ad-Hoc) mode: supported
    AP (Master) mode: unsupported
    Mesh (802.11s) mode: unsupported
    P2P mode: unsupported
    [COLOR="#FF0000"]Monitor mode: unsupported[/COLOR]
    Packet injection: unsupported

---

### Post by petros5 on 2016-03-23
Thanks for the quick reply!

lsmod:

```
Module                  Size  Used by
cfg80211              484040  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
radeon               1522941  3 
intel_rapl             18773  0 
r8712u                184158  0 
joydev                 17381  0 
snd_hda_codec_hdmi     46368  1 
x86_pkg_temp_thermal    14205  0 
snd_hda_codec_realtek    65904  1 
intel_powerclamp       14705  0 
snd_hda_intel          56611  5 
coretemp               13435  0 
snd_hda_codec         193017  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ttm                    93424  1 radeon
kvm_intel             143187  0 
kvm                   455843  1 kvm_intel
drm_kms_helper         55071  1 radeon
drm                   303102  5 ttm,drm_kms_helper,radeon
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crct10dif_pclmul       14289  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
crc32_pclmul           13113  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
i2c_algo_bit           13413  1 radeon
snd_timer              29495  2 snd_pcm,snd_seq
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
lpc_ich                21080  0 
shpchp                 37032  0 
mei_me                 18627  0 
cryptd                 20359  0 
mei                    82276  1 mei_me
mac_hid                13205  0 
video                  19476  0 
serio_raw              13462  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
ahci                   34091  2 
psmouse               106692  0 
r8169                  71677  0 
libahci                32716  1 ahci
mii                    13934  1 r8169

```

iw list: doesn't return anything.

uname -r
3.13.0-83-generic

---

### Post by chili555 on 2016-03-23
> radeon               1522941  3 
intel_rapl             18773  0 
[COLOR="#FF0000"]r8712u  [/COLOR]              184158  0 
joydev                 17381  0 
snd_hda_codec_hdmi     46368  1 
x86_pkg_temp_thermal    14205  0
<snip>You already have the driver you require.

> uname -r
3.13.0-83-generic As we suspected, your kernel version is about a decade newer than the driver file you attempted to compile.

I suggest you research and invest in a monitor mode supported device.

---

### Post by petros5 on 2016-03-23
Oh that's a bit embarrassing, sorry for the dumb question then! Thanks for the help!

---

### Post by chili555 on 2016-03-23
> **petros5 said:**
> Oh that's a bit embarrassing, sorry for the dumb question then! Thanks for the help!
Not at all. We were all beginners at one time, even me and even Linus Torvalds. Please feel free to ask again if we can help you.

[https://en.wikipedia.org/wiki/Linus_Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds)

---

