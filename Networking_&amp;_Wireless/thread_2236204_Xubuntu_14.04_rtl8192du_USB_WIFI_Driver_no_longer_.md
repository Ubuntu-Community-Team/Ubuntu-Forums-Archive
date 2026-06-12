---
title: "Xubuntu 14.04 rtl8192du USB WIFI Driver no longer working"
date: 2014-07-25
forum: Networking &amp; Wireless
---

### Post by knarf-musique on 2014-07-25
I had the [rtl8192du]("https://github.com/lwfinger/rtl8192du") driver compiled working great before a recent kernel update.
I had compliled from [https://github.com/lwfinger/rtl8192du](https://github.com/lwfinger/rtl8192du) which worked fine from 13 -14 trusty. 
But now i keep getting halted. i tired deleting and re-installing but no luck. I'm noob to compling so any help i'm greatful for. 
The USB wifi dongle im using is a _***Beklin N600 DB/F9L1101V2***_

heres what errors i keep getting in terminal:

_***WITH MAKE COMMAND:***_
root@panduh420:~# cd rtl8192du
root@panduh420:~/rtl8192du# make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-32-generic/build M=/root/rtl8192du  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CC [M]  /root/rtl8192du/os_dep/ioctl_cfg80211.o
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: ‘struct cfg80211_mgmt_tx_params’ declared inside parameter list [enabled by default]
     u64 *cookie)
     ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/root/rtl8192du/os_dep/ioctl_cfg80211.c: In function ‘cfg80211_rtw_mgmt_tx’:
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3567:21: error: dereferencing pointer to incomplete type
  size_t len = params->len;
                     ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3568:41: error: dereferencing pointer to incomplete type
  struct ieee80211_channel *chan = params->chan;
                                         ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3569:24: error: dereferencing pointer to incomplete type
  const u8 *buf = params->buf;
                        ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c: At top level:
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: initialization from incompatible pointer type [enabled by default]
  .mgmt_tx = cfg80211_rtw_mgmt_tx,
  ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’) [enabled by default]
make[2]: *** [/root/rtl8192du/os_dep/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/root/rtl8192du] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
make: *** [modules] Error 2

[U][I][B]With Make clean then Make:
[/B][/I][/U]
root@panduh420:~/rtl8192du# make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
root@panduh420:~/rtl8192du# make 
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-32-generic/build M=/root/rtl8192du  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CC [M]  /root/rtl8192du/core/rtw_cmd.o
  CC [M]  /root/rtl8192du/core/rtw_security.o
  CC [M]  /root/rtl8192du/core/rtw_debug.o
  CC [M]  /root/rtl8192du/core/rtw_io.o
  CC [M]  /root/rtl8192du/core/rtw_ioctl_set.o
  CC [M]  /root/rtl8192du/core/rtw_ieee80211.o
  CC [M]  /root/rtl8192du/core/rtw_mlme.o
  CC [M]  /root/rtl8192du/core/rtw_mlme_ext.o
  CC [M]  /root/rtl8192du/core/rtw_wlan_util.o
  CC [M]  /root/rtl8192du/core/rtw_pwrctrl.o
  CC [M]  /root/rtl8192du/core/rtw_rf.o
  CC [M]  /root/rtl8192du/core/rtw_recv.o
  CC [M]  /root/rtl8192du/core/rtw_sta_mgt.o
  CC [M]  /root/rtl8192du/core/rtw_ap.o
  CC [M]  /root/rtl8192du/core/rtw_xmit.o
  CC [M]  /root/rtl8192du/core/rtw_p2p.o
  CC [M]  /root/rtl8192du/core/rtw_sreset.o
  CC [M]  /root/rtl8192du/core/rtw_efuse.o
  CC [M]  /root/rtl8192du/hal/hal_intf.o
  CC [M]  /root/rtl8192du/hal/hal_com.o
  CC [M]  /root/rtl8192du/hal/rtl8192d_hal_init.o
  CC [M]  /root/rtl8192du/hal/rtl8192d_phycfg.o
  CC [M]  /root/rtl8192du/hal/rtl8192d_rf6052.o
  CC [M]  /root/rtl8192du/hal/rtl8192d_dm.o
  CC [M]  /root/rtl8192du/hal/rtl8192d_rxdesc.o
  CC [M]  /root/rtl8192du/hal/rtl8192d_cmd.o
  CC [M]  /root/rtl8192du/hal/usb_halinit.o
  CC [M]  /root/rtl8192du/hal/rtl8192du_led.o
  CC [M]  /root/rtl8192du/hal/rtl8192du_xmit.o
  CC [M]  /root/rtl8192du/hal/rtl8192du_recv.o
  CC [M]  /root/rtl8192du/hal/Hal8192DUHWImg.o
  CC [M]  /root/rtl8192du/hal/usb_ops_linux.o
  CC [M]  /root/rtl8192du/hal/rtl8192d_xmit.o
  CC [M]  /root/rtl8192du/os_dep/osdep_service.o
  CC [M]  /root/rtl8192du/os_dep/os_intfs.o
/root/rtl8192du/os_dep/os_intfs.c:874:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = rtw_select_queue,
  ^
/root/rtl8192du/os_dep/os_intfs.c:874:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) [enabled by default]
  CC [M]  /root/rtl8192du/os_dep/usb_intf.o
  CC [M]  /root/rtl8192du/os_dep/usb_ops_linux.o
  CC [M]  /root/rtl8192du/os_dep/ioctl_linux.o
  CC [M]  /root/rtl8192du/os_dep/xmit_linux.o
  CC [M]  /root/rtl8192du/os_dep/mlme_linux.o
  CC [M]  /root/rtl8192du/os_dep/recv_linux.o
  CC [M]  /root/rtl8192du/os_dep/ioctl_cfg80211.o
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: ‘struct cfg80211_mgmt_tx_params’ declared inside parameter list [enabled by default]
     u64 *cookie)
     ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/root/rtl8192du/os_dep/ioctl_cfg80211.c: In function ‘cfg80211_rtw_mgmt_tx’:
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3567:21: error: dereferencing pointer to incomplete type
  size_t len = params->len;
                     ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3568:41: error: dereferencing pointer to incomplete type
  struct ieee80211_channel *chan = params->chan;
                                         ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3569:24: error: dereferencing pointer to incomplete type
  const u8 *buf = params->buf;
                        ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c: At top level:
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: initialization from incompatible pointer type [enabled by default]
  .mgmt_tx = cfg80211_rtw_mgmt_tx,
  ^
/root/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’) [enabled by default]
make[2]: *** [/root/rtl8192du/os_dep/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/root/rtl8192du] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
make: *** [modules] Error 2


So I'm Confused as to what to do to fix this. I tired posting in the github repo first but no repsonse. =/ 
Am i better off trying to ndiwrapper install it?

---

### Post by knarf-musique on 2014-07-25
does anyone know if downgrading the linux headers will help? it stopped working after i updated kernels. have no idea if thats the issue. 
I'm on amd 64, xubuntu 14.04.

---

### Post by chili555 on 2014-07-25
I see there are two branches here. I suggest you try:```
wget https://github.com/lwfinger/rtl8192du/archive/kernel-version.zip
unzip kernel-version.zip
cd rtl8192du-kernel-version
make 
sudo make install
sudo modprobe 8192du
```It 'makes' without even one warning on my fully updated 14.04 system.

---

### Post by wb8dxx on 2014-09-09
Same errors as above -- building with a module I downloaded to a Windoze partition and then copied over to my Linux partition. I am running Ubuntu 14.04 64 bit. To me the errors look like what I would get from a mismatch between headers and .c files. Output from make:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-24-generic/build M=/home
/patricia/rtl8192du-master  
modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  
CC [M]  /home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.o
/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.c:3556:5: warning: ‘struct cfg80211_mgmt_tx_params’ declared inside parameter list [enabled by default]
     u64 *cookie)
     ^/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.c:3556:5: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.c: In function ‘cfg80211_rtw_mgmt_tx’:
/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.c:3567:21: error: dereferencing pointer to incomplete type
  size_t len = params->len;
                     ^
/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.c:3568:41: error: dereferencing pointer to incomplete type
  struct ieee80211_channel *chan = params->chan;
                                         ^
/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.c:3569:24: error: dereferencing pointer to incomplete type
  const u8 *buf = params->buf;
                        ^
/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.c: At top level:
/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.c:3650:2: warning: initialization from incompatible pointer type [enabled by default]
  .mgmt_tx = cfg80211_rtw_mgmt_tx,
  ^
/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.c:3650:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’) [enabled by default]
make[2]: *** [/home/patricia/rtl8192du-master/os_dep/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/home/patricia/rtl8192du-master] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [modules] Error 2

---

### Post by chili555 on 2014-09-09
> /home/patricia/[COLOR="#FF0000"]rtl8192du-master[/COLOR]Did you try the other branch, kernel-version, as I suggested above? I just downloaded and extracted it and it 'makes' with no warnings and no errors.

> /home/chili/Downloads/rtl8192du-kernel-version

---

### Post by knarf-musique on 2015-01-13
After a kernel update i ran make clean and tried to re-install but now im getting a new error. I need to stop kernel updating lol....

> 
panduh@panduh:~/rtl8192du-kernel-version$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.16.0-29-generic/build M=/home/panduh/rtl8192du-kernel-version  modules
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-29-generic'
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_ap.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_cmd.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_debug.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_efuse.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_ieee80211.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_io.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_ioctl_set.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_mlme.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_mlme_ext.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_pwrctrl.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_recv.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_rf.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_security.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_sta_mgt.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_wlan_util.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/core/rtw_xmit.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/hal_com.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/hal_intf.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192d_cmd.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192d_dm.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192d_hal_init.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192d_phycfg.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192d_rf6052.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192d_rxdesc.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192d_xmit.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192du_led.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192du_xmit.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/rtl8192du_recv.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/Hal8192DUHWImg.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/usb_halinit.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/hal/usb_ops_linux.o
  CC [M]  /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.o
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_indicate_sta_assoc&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2197:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(padapter->rtw_wdev, freq, 0, pmgmt_frame, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_indicate_sta_disassoc&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2244:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(padapter->rtw_wdev, freq, 0, mgmt_buf, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_action_p2p&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2766:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(padapter->rtw_wdev, freq, 0, pmgmt_frame, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_p2p_action_public&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2787:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(padapter->rtw_wdev, freq, 0, pmgmt_frame, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_action&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2812:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(adapter->rtw_wdev, freq, 0, frame, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
scripts/Makefile.build:257: recipe for target '/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.o' failed
make[2]: *** [/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.o] Error 1
Makefile:1345: recipe for target '_module_/home/panduh/rtl8192du-kernel-version' failed
make[1]: *** [_module_/home/panduh/rtl8192du-kernel-version] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-29-generic'
Makefile:98: recipe for target 'modules' failed
make: *** [modules] Error 2
panduh@panduh:~/rtl8192du-kernel-version$ sudo make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.16.0-29-generic/build M=/home/panduh/rtl8192du-kernel-version  modules
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-29-generic'
  CC [M]  /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.o
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_indicate_sta_assoc&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2197:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(padapter->rtw_wdev, freq, 0, pmgmt_frame, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_indicate_sta_disassoc&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2244:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(padapter->rtw_wdev, freq, 0, mgmt_buf, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_action_p2p&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2766:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(padapter->rtw_wdev, freq, 0, pmgmt_frame, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_p2p_action_public&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2787:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(padapter->rtw_wdev, freq, 0, pmgmt_frame, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_action&#8217;:
/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:2812:2: error: too few arguments to function &#8216;cfg80211_rx_mgmt&#8217;
  cfg80211_rx_mgmt(adapter->rtw_wdev, freq, 0, frame, frame_len, flags);
  ^
In file included from /home/panduh/rtl8192du-kernel-version/include/osdep_service.h:52:0,
                 from /home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.c:19:
include/net/cfg80211.h:4445:6: note: declared here
 bool cfg80211_rx_mgmt(struct wireless_dev *wdev, int freq, int sig_dbm,
      ^
scripts/Makefile.build:257: recipe for target '/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.o' failed
make[2]: *** [/home/panduh/rtl8192du-kernel-version/os_dep/ioctl_cfg80211.o] Error 1
Makefile:1345: recipe for target '_module_/home/panduh/rtl8192du-kernel-version' failed
make[1]: *** [_module_/home/panduh/rtl8192du-kernel-version] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-29-generic'
Makefile:98: recipe for target 'modules' failed
make: *** [modules] Error 2
panduh@panduh:~/rtl8192du-kernel-version$ 


---

### Post by chili555 on 2015-01-13
> Makefile:1345: recipe for target '_module_/home/panduh/rtl8192du-kernel-version' failed
make[1]: *** [_module_/home/panduh/rtl8192du-kernel-version] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-29-generic'
Makefile:98: recipe for target 'modules' failed
make: *** [modules] Error 2
panduh@panduh:~/rtl8192du-kernel-version$This makes *perfectly* on my 3.16.0-29 system:```
git clone https://github.com/lwfinger/rtl8192du.git
cd rtl8192du
make
sudo make install 
sudo modprobe 8192du
```

---

### Post by knarf-musique on 2015-01-30
Thanks [**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=35909") your my hero! ):P

---

