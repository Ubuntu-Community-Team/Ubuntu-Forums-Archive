---
title: "No Wi-Fi Adapter found Ubuntu 18.04.01 HP 15 Pavilion-cw0xxx"
date: 2019-01-25
forum: Networking &amp; Wireless
---

### Post by volterra-project-16 on 2019-01-25
Hi, I have a problem with the WiFi driver (Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter). I have the Linux kernel 5.0.0-050000rc3-lowlatency (64 bits) (I upgrade it manually, I have 4.15.0-29-generic again (I have reinstall Ubuntu).). 
I have tried several "generic" solutions that I found in this forum, but if they do not throw me an error, some commands can no longer be used. I downloaded a couple of files that apparently are RTL8821CE drivers but doing a "make" error.

```
victor@victor-HP-Pavilion-Laptop-15-cw0xxx:~/rtl8821ce$ sudo make all
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.0.0-050000rc3-lowlatency/build M=/home/victor/rtl8821ce  modules
make[1]: Entering directory '/usr/src/linux-headers-5.0.0-050000rc3-lowlatency'
  CC [M]  /home/victor/rtl8821ce/os_dep/linux/rtw_android.o
In file included from /home/victor/rtl8821ce/include/drv_types.h:35:0,
                 from /home/victor/rtl8821ce/os_dep/linux/rtw_android.c:25:
/home/victor/rtl8821ce/include/wifi.h:1019:0: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /home/victor/rtl8821ce/include/osdep_service_linux.h:86:0,
                 from /home/victor/rtl8821ce/include/osdep_service.h:48,
                 from /home/victor/rtl8821ce/include/drv_types.h:32,
                 from /home/victor/rtl8821ce/os_dep/linux/rtw_android.c:25:
./include/linux/ieee80211.h:1444:0: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
/home/victor/rtl8821ce/os_dep/linux/rtw_android.c: In function &#8216;rtw_android_priv_cmd&#8217;:
/home/victor/rtl8821ce/os_dep/linux/rtw_android.c:629:62: error: macro "access_ok" passed 3 arguments, but takes just 2
  if (!access_ok(VERIFY_READ, priv_cmd.buf, priv_cmd.total_len)) {
                                                              ^
/home/victor/rtl8821ce/os_dep/linux/rtw_android.c:629:7: error: &#8216;access_ok&#8217; undeclared (first use in this function)
  if (!access_ok(VERIFY_READ, priv_cmd.buf, priv_cmd.total_len)) {
       ^~~~~~~~~
/home/victor/rtl8821ce/os_dep/linux/rtw_android.c:629:7: note: each undeclared identifier is reported only once for each function it appears in
scripts/Makefile.build:276: recipe for target '/home/victor/rtl8821ce/os_dep/linux/rtw_android.o' failed
make[2]: *** [/home/victor/rtl8821ce/os_dep/linux/rtw_android.o] Error 1
Makefile:1553: recipe for target '_module_/home/victor/rtl8821ce' failed
make[1]: *** [_module_/home/victor/rtl8821ce] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.0.0-050000rc3-lowlatency'
Makefile:1902: recipe for target 'modules' failed
make: *** [modules] Error 2


```

---

### Post by kc1di on 2019-01-26
The answers in this ask ubuntu post may be of help : [https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04]("https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04")

---

### Post by praseodym on 2019-01-26
I think kernel 5 is not supported yet from that repository?! Contact the maintainer

---

### Post by volterra-project-16 on 2019-01-26
I upgrade it manually, I have 4.15.0-29-generic again (I have reinstall Ubuntu).

---

### Post by volterra-project-16 on 2019-01-26
Thanks, I will try it.

---

### Post by volterra-project-16 on 2019-01-26
I am trying this: [https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce](https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce)

And I get this with 'make' command: 

victor@victor-HP-Pavilion-Laptop-15-cw0xxx:~/Descargas/rtl8821ce$ make
/bin/sh: 1: cc: not found
(standard_in) 1: syntax error
Makefile:821: /home/victor/Downloads/rtl8821ce/rtl8821c.mk: No such file or directory
make: *** No rule to make target '/home/victor/Downloads/rtl8821ce/rtl8821c.mk'.  Stop.

---

### Post by volterra-project-16 on 2019-01-26
[https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04](https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04) 
That's perfectly worked for me. ¡THANKS! I solved the trouble.

---

### Post by kc1di on 2019-01-26
Glad it worked for you - Enjoy :)

---

### Post by praseodym on 2019-01-26
So, you installed via dkms, not compiling by "make"? Maybe THAT is also interesting for the maintainer as well ;)

Edit: If it was installed for kernel 5

---

