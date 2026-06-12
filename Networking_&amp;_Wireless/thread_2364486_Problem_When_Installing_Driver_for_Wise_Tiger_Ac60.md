---
title: "Problem When Installing Driver for Wise Tiger Ac600Mbps Wifi Adapter in 16.04LTS"
date: 2017-06-23
forum: Networking &amp; Wireless
---

### Post by hey--joe on 2017-06-23
I have the same problem as the link here [https://ubuntuforums.org/showthread.php?t=2339960.](https://ubuntuforums.org/showthread.php?t=2339960.)  I found many similarities but cannot solve it. My system is Ubuntu 16.04LTS with 4.8.0-56-generic. After I did ```
sudo  apt-get install rtl8812au-dkms
``` I got exactly the same thing in the link like  > Consult  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log for  more information. What should I do next? 
 I  also tried the following:

[LIST]
[*]```
sudo modprobe 8812au
``` the output is  ```
modprobe: ERROR: could not insert '8812au': Required key not  available
``` 
[/LIST]
 
[LIST]
[*]```
lsmod | grep 8812
``` no output; 
[/LIST]
 
[LIST]
[*]```
modinfo 8812au | grep 0811
``` the output is ```
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
``` 
[/LIST]
 
[LIST]
[*]```
dmesg | grep 8812
``` no output. 
[/LIST]
As for the > cat  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log The output is ```
DKMS make.log for rtl8812au-4.3.8.12175.20140902+dfsg for kernel 4.8.0-56-generic (x86_64)
Fri Jun 23 14:46:15 EDT 2017
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.8.0-56-generic/build M=/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-56-generic'
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_ieee80211.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_mlme.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_mlme_ext.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_wlan_util.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_vht.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_pwrctrl.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_rf.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_recv.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_sta_mgt.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_ap.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_xmit.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_p2p.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_tdls.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_br_ext.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_iol.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_sreset.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_btcoex.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_beamforming.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/rtw_odm.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/core/efuse/rtw_efuse.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/osdep_service.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/os_intfs.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/usb_intf.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/usb_ops_linux.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/ioctl_linux.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/xmit_linux.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/mlme_linux.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/recv_linux.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/rtw_cfgvendor.o
  CC [M]  /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/rtw_android.o
/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/rtw_android.c: In function ‘rtw_android_priv_cmd’:
/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/rtw_android.c:577:6: error: implicit declaration of function ‘is_compat_task’ [-Werror=implicit-function-declaration]
  if (is_compat_task()) {
      ^
cc1: some warnings being treated as errors
scripts/Makefile.build:289: recipe for target '/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/rtw_android.o' failed
make[2]: *** [/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/rtw_android.o] Error 1
Makefile:1491: recipe for target '_module_/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build' failed
make[1]: *** [_module_/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-56-generic'
Makefile:1459: recipe for target 'modules' failed
make: *** [modules] Error 2

```

---

### Post by chili555 on 2017-06-23
I think there was a change in the 4.8 kernel that prevents the 4.3.8.12175 version from compiling correctly. I suggest that you try this instead: [https://askubuntu.com/questions/920188/ourlink-ver-realtech-usb-adaptor-not-working/920191#920191](https://askubuntu.com/questions/920188/ourlink-ver-realtech-usb-adaptor-not-working/920191#920191)> Required key not  availablePlease see: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by hey--joe on 2017-06-23
Nice!! I used the driver from github and followed the instructions in the second link [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules) to disabled the secure boot in BIOS setting. Now I successfully run```
sudo modprobe 8812au
```and the wifi adapter is set up. Thank you very much!

---

### Post by chili555 on 2017-06-23
Awesome! Glad it's working. Please use thread tools at the top of the thread to mark Solved. The searchers will appreciate it.

---

