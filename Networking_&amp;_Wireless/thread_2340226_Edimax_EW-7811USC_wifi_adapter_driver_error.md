---
title: "Edimax EW-7811USC wifi adapter driver error"
date: 2016-10-16
forum: Networking &amp; Wireless
---

### Post by waxcan on 2016-10-16
Hi folks,
Not sure of the place to post this as it relates to third party software, but I think the error may be in my lack of Linux knowledge.

The Edimax EW-7811USC comes wwith drivers that others seem to have no problem installing.

Thanks in advance for your help and apologies if I am lacking in details. The error is at the bottom of the code which triggered after I tried sudo make, and it threw make: *** [modules] Error 2

Once I extract the tar.gz file to /home/darren I can successfully follow the instructions in the manual

```
tar vxzf EW-7811USC_linux_v4.3.14_13455.20150212_BTCOEX20150128-51.tar.gz

cd rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51


```

it failed on 

```
sudo make
```

with the error code below 

```
root@ubuntudell:~/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51# sudo makemake ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-34-generic/build M=/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-34-generic'
  CC [M]  /home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o
In file included from /home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:95:0,
                 from /home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h:412:13: error: &#8216;file_path&#8217; redeclared as different kind of symbol
 extern char file_path[PATH_LENGTH_MAX];
             ^
In file included from include/linux/compat.h:15:0,
                 from include/linux/ethtool.h:15,
                 from include/linux/netdevice.h:42,
                 from /home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h:35,
                 from /home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h:41,
                 from /home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:32,
                 from /home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
include/linux/fs.h:2572:14: note: previous declaration of &#8216;file_path&#8217; was here
 extern char *file_path(struct file *, char *, int);
              ^
In file included from /home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h:65:0,
                 from /home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:22:
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c: In function &#8216;btinfo_evt_dump&#8217;:
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3293:2: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
  DBG_871X_SEL_NL(sel, "cid:0x%02x, len:%u\n", info->cid, info->len);
  ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3296:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "byte2:%s%s%s%s%s%s%s%s\n"
   ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3308:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "retry_cnt:%u\n", info->retry_cnt);
   ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3311:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "rssi:%u\n", info->rssi);
   ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h:242:7: note: in expansion of macro &#8216;_seqdump&#8217;
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c:3314:3: note: in expansion of macro &#8216;DBG_871X_SEL_NL&#8217;
   DBG_871X_SEL_NL(sel, "byte5:%s%s\n"
   ^
scripts/Makefile.build:258: recipe for target '/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o' failed
make[2]: *** [/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o] Error 1
Makefile:1403: recipe for target '_module_/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51' failed
make[1]: *** [_module_/home/darren/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-34-generic'
Makefile:1551: recipe for target 'modules' failed
make: *** [modules] Error 2
root@ubuntudell:~/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51#



```




update:
Here is a link to the EW-7811USC [manual]("https://drive.google.com/open?id=0B8UyvnNEbGhRS0xWTGQyZkZLUTg") and the [driver]("https://drive.google.com/open?id=0B8UyvnNEbGhRb0lhS19QWUEtNnc"). I substituted the tar vxzf FILENAME with the updated one supplied on the CD which had a different filename. I also tried with the latest driver on the Edimax site but still had the make error 2.

Thanks!

---

### Post by Geoffrey_Arndt on 2016-10-17
Hmm, I have that same exact model and same chipset . . . just plugged it in and it found my network.   No need to install drivers as kernel level support was added to ubuntu starting with version 12.04.   Am running 16.04.1 and haven't tested it yet but will do some tomorrow and advise if I see a different outcome.

---

### Post by howefield on 2016-10-17
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

### Post by praseodym on 2016-10-17
Why not using the one from the repos?
```

sudo apt-get install rtl8812au-dkms
```

---

### Post by waxcan on 2016-10-17
Thanks mate, I'll check again myself and write back.

---

### Post by Geoffrey_Arndt on 2016-10-17
My identical edimax still plays nice with Ubuntu 16.04.1 on an Acer Travelmate 4830T (no module/driver install or compiling needed).     It shows both network adapters (built in Intel wireless) and the Realtek/Edimax w/rtl8812au.   Could different firmware be on these devices?   Would be interesting to find out.   Perhaps same reason the familiy of wireless Panda devices just work out of the box (plug & Play) . . . for same chipset in some devices.   Firmware also?

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

