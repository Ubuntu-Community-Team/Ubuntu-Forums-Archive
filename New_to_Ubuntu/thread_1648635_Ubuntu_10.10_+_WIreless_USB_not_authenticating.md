---
title: "Ubuntu 10.10 + WIreless USB not authenticating"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by ghettonerd on 2010-12-19
I am running driver net8912su under ndiswrapper (xp versio of the driver that came with my usb) and i cannot get my connection to authenticate. I am 100% sure my ssid and password are correct, i have tried connecting with both wep and wpa. my usb did come with linux drivers but i'm a noob and have no clue how to compile from souce, i keep getting erros when i make the file, heres some setting maybe someone can help. 

 >lsusb
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter




>iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



in my task bar uptop i can see the available networks, i just cannot connect PLEASE HELP

---

### Post by ghettonerd on 2010-12-19
here is waht happens when i try to comple

lozano@lozano-ubuntu:~$ cd '/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229' 
lozano@lozano-ubuntu:~/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.35-23-generic/build M=/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/cmd/rtl871x_cmd.o
In file included from /home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/cmd/rtl871x_cmd.c:21:
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h: In function ‘thread_enter’:
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:348: error: implicit declaration of function ‘daemonize’
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:349: error: implicit declaration of function ‘allow_signal’
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:349: error: ‘SIGTERM’ undeclared (first use in this function)
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:349: error: (Each undeclared identifier is reported only once
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:349: error: for each function it appears in.)
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h: In function ‘flush_signals_thread’:
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:356: error: implicit declaration of function ‘signal_pending’
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:358: error: implicit declaration of function ‘flush_signals’
In file included from include/linux/usb.h:21,
                 from /home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_intf.h:13,
                 from /home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/rtl871x_io.h:7,
                 from /home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/drv_types.h:58,
                 from /home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/cmd/rtl871x_cmd.c:22:
include/linux/sched.h: At top level:
include/linux/sched.h:2008: warning: conflicting types for ‘flush_signals’
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:358: note: previous implicit declaration of ‘flush_signals’ was here
include/linux/sched.h:2115: warning: conflicting types for ‘daemonize’
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:348: note: previous implicit declaration of ‘daemonize’ was here
include/linux/sched.h:2316: error: static declaration of ‘signal_pending’ follows non-static declaration
/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/include/osdep_service.h:356: note: previous implicit declaration of ‘signal_pending’ was here
make[2]: *** [/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/lozano/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [modules] Error 2
lozano@lozano-ubuntu:~/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091229$

---

### Post by nbolds442 on 2010-12-21
I am having the same issue with a new install of 10.10 on a laptop with a builtin wireless.  Have you had any luck fixing the issue?

---

### Post by Sonicrulz12 on 2010-12-21
has anybody tried right clicking on the wi-fi sign on the panel and enabled networking and wireless? hopefully this helps you

---

### Post by Sonicrulz12 on 2010-12-21
do this by right-clicking the wi-fi sign

---

### Post by davidmohammed on 2010-12-21
there is a long [thread on this issue]("http://ubuntuforums.org/showthread.php?t=1620923&page=6") - reading from the end, it seems to have been solved.

---

