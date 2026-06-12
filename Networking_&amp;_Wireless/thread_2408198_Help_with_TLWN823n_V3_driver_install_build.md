---
title: "Help with TLWN823n V3 driver install build"
date: 2018-12-15
forum: Networking &amp; Wireless
---

### Post by mariofanboy-21 on 2018-12-15
Hello, a few days ago, I got this USB wifi dongle  and when I try to compile the driver for it, I get this message

```
cardin@ubuntu:~$ cd /home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047
cardin@ubuntu:~/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047$ make clean
#make -C /lib/modules/4.15.0-42-generic/build M=/home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047 clean
cd hal ; rm -fr */*/*/*.mod.c */*/*/*.mod */*/*/*.o */*/*/.*.cmd */*/*/*.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
cardin@ubuntu:~/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/4.15.0-42-generic/build M=/home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-42-generic'
  CC [M]  /home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047/core/rtw_cmd.o
In file included from /home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047/include/osdep_service.h:47:0,
                 from /home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047/include/drv_types.h:27,
                 from /home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047/core/rtw_cmd.c:17:
/home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
/home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047/include/osdep_service_linux.h:299:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^~
/home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047/include/osdep_service_linux.h:300:2: error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;_init_timer&#8217;? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047/core/rtw_cmd.o' failed
make[2]: *** [/home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047/core/rtw_cmd.o] Error 1
Makefile:1551: recipe for target '_module_/home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047' failed
make[1]: *** [_module_/home/cardin/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-42-generic'
Makefile:1828: recipe for target 'modules' failed
cardin@ubuntu:~/Desktop/rtl8192EU_WiFi_linux_v5.2.19.1_25633.20171222_COEX20171113-0047$
```

---

### Post by jeremy31 on 2018-12-15
Moved to Networking & Wireless

Post results for ```
lsusb; modinfo rtl8xxxu | grep -i alias
```

---

### Post by mariofanboy-21 on 2018-12-15
```
Bus 001 Device 006: ID 2357:0109
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 0461:4d22 Primax Electronics, Ltd
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
alias:          usb:v0BDAp818Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019pAB33d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2357p0107d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v7392p7822d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v4855p0091d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2357p0100d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v20F4p624Dd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p330Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p3309d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p3307d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E66p0020d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E66p0019d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp2E2Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0846pF001d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0846p9021d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v07B8p8178d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v07AAp0056d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0789p016Dd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0DF6p0070d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0DF6p0061d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p17ABd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v06F8pE035d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0586p341Fd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v050Dp2103d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v050Dp2102d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04BBp0950d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019p1201d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:vCDABp8010d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v4856p0091d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v4855p0090d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019pED17d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019p4902d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p330Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v13D3p3357d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v103Cp1629d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0EB0p9071d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0DF6p0052d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp5088d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp1E1Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p17BAd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0846p9041d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v07B8p8189d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v06F8pE033d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v050Dp1102d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04BBp094Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1058p0631d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8177d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8170d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8191d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p3308d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v20F4p648Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v050Dp1004d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v7392p7811d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8178d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8176d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB720d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2357p0109d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p3319d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2357p0108d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp818Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp0724d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp1724d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8724d*dc*dsc*dp*icFFiscFFipFFin*
```

---

### Post by jeremy31 on 2018-12-15
Why are you trying to compile a module when there is one in the kernel?

---

### Post by mariofanboy-21 on 2018-12-15
Because the module in the kernal is glitchy.  It keeps on cutting  in and out unlike when I try it in windows.

---

### Post by jeremy31 on 2018-12-15
Ok, I think that can be fixed
```
sudo apt install git dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```
Reboot

---

### Post by mariofanboy-21 on 2018-12-15
[COLOR=#000000]Because the module in the kernal is glitchy. It keeps on cutting in and out unlike when I try it in windows. (Please delete the first instance of this  statement.)[/COLOR]

---

### Post by mariofanboy-21 on 2018-12-15
Thanks. It worked like a charm

---

### Post by csatlas on 2019-11-10
> **jeremy31 said:**
> Ok, I think that can be fixed
```
sudo apt install git dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```
Reboot

  problem solved for me too, Ubuntu18.04 tp-link usb dongle signal too low, thank you!

---

### Post by uRock on 2019-11-10
Back to sleep old thread.

---

