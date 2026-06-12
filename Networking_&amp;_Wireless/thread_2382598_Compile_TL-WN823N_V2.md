---
title: "Compile TL-WN823N V2"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by coopebd on 2018-01-15
Hello All,  

I'm attempting to install the driver TL-WN823N on Ubuntu 14.04LTS.  My issue is I don't know what any of the following means:
ARCH ?= $(SUBARCH) 
CROSS_COMPILE ?=
KVER := $(shell uname -r)

I need to edit this items in the makefile.c file.  Any help would be greatly appreciated.  Thank you.

---

### Post by steeldriver on 2018-01-15
Hello and welcome to the forums

Unless you are running on an uncommon hardware platform (or actually are cross-compiling) these kinds of things don't usually need to be edited in my experience

What is the actual issue you are having? where did you get the source code that you are trying to compile?

---

### Post by coopebd on 2018-01-15
Thanks steeldriver for your response.  The instruction that came with the driver said I should modify these.  Initially i thought i didn't need too but once i attempted to install i got some errors. make[2] *** [/home/research/Downloads/Driver/core/rtw_cmd.0] Error 1
make [1] ***[_module_/home/research/Downloads/Driver] Error2  
make [1] Leaving directory '/usr/src/linux-headers-4.4.0-101-generic'
make *** [modules] Error 2

So when I saw that i thought i should have make changes to that makefile.c .  I got the error message using ~/Downloads/Drivers$ make   .  I'm i looking at this all wrong?

---

### Post by steeldriver on 2018-01-15
It's hard to guess what the issue is based on that fragment - if you can provide more detail about the source (such as an exact version - or ideally a link to download the source) I will take a look

Most often with network drivers the issue is that they are specific to a particular kernel version and can't be built against other kernels

---

### Post by jeremy31 on 2018-01-15
coopebd, please post the results from terminal for 
```
lsusb
```
With the wifi dongle plugged in

---

### Post by coopebd on 2018-01-16
research@researchcameras-MS-7A71:~$ lsusb


Bus 002 Device 002: ID 0951:1666 Kingston Technology DataTraveler G4


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


Bus 001 Device 004: ID 2357:0109  


Bus 001 Device 006: ID 046d:c077 Logitech, Inc. M105 Optical Mouse


Bus 001 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


research@researchcameras-MS-7A71:~$

---

### Post by chili555 on 2018-01-16
Isn't the driver already present in 14.04?```
modinfo rtl8192cu | grep 0109
```Since, as we suspect, there is already a driver (and maybe two!!) in 14.04, installing an older, rusty driver isn't going to help anything. What is your exact problem?

By the way, we'd also like to see:```
modinfo rtl8xxxu | grep 0109
```

---

### Post by jeremy31 on 2018-01-16
See [https://askubuntu.com/a/813034/300665](https://askubuntu.com/a/813034/300665)
Either install method posted by Pilot6 should work

---

### Post by coopebd on 2018-01-16
This is the link to for the wireless dongle [http://static.tp-link.com/TL-WN823N_V2_User%20Guide.pdf](http://static.tp-link.com/TL-WN823N_V2_User%20Guide.pdf)

---

### Post by chili555 on 2018-01-16
> **coopebd said:**
> This is the link to for the wireless dongle [http://static.tp-link.com/TL-WN823N_V2_User%20Guide.pdf](http://static.tp-link.com/TL-WN823N_V2_User%20Guide.pdf)Please see my post #7.

---

### Post by coopebd on 2018-01-16
When i attempt to compile the driver it returns errors:

```
research@researchcameras-MS-7A71:~/Downloads/Driver$ sudo make
[sudo] 
password for research: 
"******************************************"
"
NO SKRC,we will use default KSRC"
"******************************************"
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-101-generic/build M=/home/research/Downloads/Driver  modules
make[1]: Entering directory `/usr/src/linux-headers-4.4.0-101-generic'
"
******************************************"
"
NO SKRC,we will use default KSRC"
"
******************************************"
  
  CC [M]  /home/research/Downloads/Driver/core/rtw_cmd.o


In file included from /home/research/Downloads/Driver/include/drv_types.h:95:0,
                
		 from /home/research/Downloads/Driver/core/rtw_cmd.c:22:


/home/research/Downloads/Driver/include/hal_com.h:413:13: error: &#8216;file_path&#8217; redeclared 
as different kind of symbol
 extern char file_path[PATH_LENGTH_MAX];
            
 
  ^
In file included from include/linux/seq_file.h:10:0,
                 
		from include/linux/pinctrl/consumer.h:17,
                
	        from include/linux/pinctrl/devinfo.h:21,
                 
                from include/linux/device.h:24,
                 
		from include/linux/dmaengine.h:20,
                 
		from include/linux/netdevice.h:38,
                 
		from /home/research/Downloads/Driver/include/osdep_service_linux.h:35,
                 
		from /home/research/Downloads/Driver/include/osdep_service.h:41,
                 
		from /home/research/Downloads/Driver/include/drv_types.h:32,
                 
		from /home/research/Downloads/Driver/core/rtw_cmd.c:22:


include/linux/fs.h:2610:14: note: previous declaration of &#8216;file_path&#8217; was here
 extern char *file_path(struct file *, char *, int);
           


   ^
In file included from /home/research/Downloads/Driver/include/drv_types.h:65:0,
                
                     from /home/research/Downloads/Driver/core/rtw_cmd.c:22:


/home/research/Downloads/Driver/core/rtw_cmd.c: In function &#8216;btinfo_evt_dump&#8217;:


/home/research/Downloads/Driver/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
     
             
   ^
/home/research/Downloads/Driver/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
   
	 if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
      
   ^
/home/research/Downloads/Driver/core/rtw_cmd.c:3293:2: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
  DBG_871X_SEL_NL(sel, "cid:0x%02x, len:%u\n", info->cid, info->len);
  ^
/home/research/Downloads/Driver/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                  
   ^
/home/research/Downloads/Driver/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    
       if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       


   ^
/home/research/Downloads/Driver/core/rtw_cmd.c:3296:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "byte2:%s%s%s%s%s%s%s%s\n"
   
   ^
/home/research/Downloads/Driver/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
               
   ^
/home/research/Downloads/Driver/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
   
       if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
      
   ^
/home/research/Downloads/Driver/core/rtw_cmd.c:3308:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "retry_cnt:%u\n", info->retry_cnt);
   
   ^
/home/research/Downloads/Driver/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   
   ^
/home/research/Downloads/Driver/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
   
       if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       
   ^
/home/research/Downloads/Driver/core/rtw_cmd.c:3311:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "rssi:%u\n", info->rssi);
   
   ^
/home/research/Downloads/Driver/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   
   ^
/home/research/Downloads/Driver/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    
      if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       
   ^
/home/research/Downloads/Driver/core/rtw_cmd.c:3314:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "byte5:%s%s\n"
   


      ^
make[2]: *** [/home/research/Downloads/Driver/core/rtw_cmd.o] Error 1
       
make[1]: *** [_module_/home/research/Downloads/Driver] Error 2
       
make[1]: Leaving directory `/usr/src/linux-headers-4.4.0-101-generic'
make: *** [modules] Error 2
research@researchcameras-MS-7A71:~/Downloads/Driver$
```

---

### Post by jeremy31 on 2018-01-16
Please stop trying to compile the source from Realtek and just use Pilot6 PPA or the source from Mange's github
I added the following commit 18 months ago
```
/*===TPLINK ID===========*/
+	{USB_DEVICE(0x2357, 0x0107),.driver_info = RTL8192E}, /* TP-Link - Cameo */
+	{USB_DEVICE(0x2357, 0x0108),.driver_info = RTL8192E}, /* TP-Link - Cameo */
+	{USB_DEVICE(0x2357, 0x0109),.driver_info = RTL8192E}, /* TP-Link - Cameo */
```

---

### Post by coopebd on 2018-01-16
Are you referring to this
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms

If so i did try and it doesn't work either.

---

### Post by coopebd on 2018-01-16
How do I do that.

---

### Post by jeremy31 on 2018-01-16
See the wireless script link in my signature and post results, also include terminal results for ```
dkms status
```

---

### Post by jeremy31 on 2018-01-17
> **coopebd said:**
> Are you referring to this
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms

If so i did try and it doesn't work either.

If you did try that you need to go into UEFI/BIOS settings and make sure Secure Boot is disabled

---

