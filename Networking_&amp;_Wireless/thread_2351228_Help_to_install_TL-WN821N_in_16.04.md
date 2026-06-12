---
title: "Help to install TL-WN821N in 16.04"
date: 2017-02-01
forum: Networking &amp; Wireless
---

### Post by xld on 2017-02-01
Hi. I also got the same problem with installing tp-link TL-WN821N V5 on Ubuntu 16.04. I followed steps on [http://www.tp-link.com/us/download/TL-WN821N.html#Driver](http://www.tp-link.com/us/download/TL-WN821N.html#Driver) and got stuck on 

```
sudo make
```

```


&#10140; sudo make
"******************************************"
"NO SKRC,we will use default KSRC"
"******************************************"
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-59-generic/build M=/home/sean/Documents/tl-wn821n-v5-160315-linux  modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-59-generic'
"******************************************"
"NO SKRC,we will use default KSRC"
"******************************************"
  CC [M]  /home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.o
In file included from /home/sean/Documents/tl-wn821n-v5-160315-linux/include/drv_types.h:95:0,
                 from /home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.c:22:
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/hal_com.h:413:13: error: ‘file_path’ redeclared as different kind of symbol
 extern char file_path[PATH_LENGTH_MAX];
             ^
In file included from include/linux/compat.h:15:0,
                 from include/linux/ethtool.h:16,
                 from include/linux/netdevice.h:42,
                 from /home/sean/Documents/tl-wn821n-v5-160315-linux/include/osdep_service_linux.h:35,
                 from /home/sean/Documents/tl-wn821n-v5-160315-linux/include/osdep_service.h:41,
                 from /home/sean/Documents/tl-wn821n-v5-160315-linux/include/drv_types.h:32,
                 from /home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.c:22:
include/linux/fs.h:2603:14: note: previous declaration of ‘file_path’ was here
 extern char *file_path(struct file *, char *, int);
              ^
In file included from /home/sean/Documents/tl-wn821n-v5-160315-linux/include/drv_types.h:65:0,
                 from /home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.c:22:
/home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.c: In function ‘btinfo_evt_dump’:
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.c:3293:2: note: in expansion of macro ‘DBG_871X_SEL_NL’
  DBG_871X_SEL_NL(sel, "cid:0x%02x, len:%u\n", info->cid, info->len);
  ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.c:3296:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "byte2:%s%s%s%s%s%s%s%s\n"
   ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.c:3308:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "retry_cnt:%u\n", info->retry_cnt);
   ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.c:3311:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "rssi:%u\n", info->rssi);
   ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.c:3314:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "byte5:%s%s\n"
   ^
scripts/Makefile.build:258: recipe for target '/home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.o' failed
make[2]: *** [/home/sean/Documents/tl-wn821n-v5-160315-linux/core/rtw_cmd.o] Error 1
Makefile:1420: recipe for target '_module_/home/sean/Documents/tl-wn821n-v5-160315-linux' failed
make[1]: *** [_module_/home/sean/Documents/tl-wn821n-v5-160315-linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-59-generic'
Makefile:1696: recipe for target 'modules' failed
make: *** [modules] Error 2



```

I also followed the instructions here [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes) but still can't use the wireless adapter.

Hoping for your reply. 

Thanks

---

### Post by howefield on 2017-02-01
Post moved to own thread.

---

### Post by jeremy31 on 2017-02-01
Please post results for
```
lsusb
```

---

### Post by xld on 2017-02-01
Here are the results of 

> 
$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 8087:07dc Intel Corp. 
Bus 003 Device 009: ID 2357:0107  
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




---

### Post by jeremy31 on 2017-02-01
This should work for that one
```
sudo apt-get install git build-essential dkms
```

Then we can clone Mange's github code

```
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
```

Then use dkms to add it ```
sudo dkms add ./rtl8192eu-linux-driver
```

Then install

```
sudo dkms install -m rtl8192eu -v 1.0
```

Reboot

---

