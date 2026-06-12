---
title: "RTL-8185 compile issue"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by macka` on 2007-04-22
Hi there, 
installed Feisty Fawn, likin' it so far.

Got me a RTL8185 and i have managed to try and use Ndiswrapper, but the little gui interface says the hardware is not installed? dunno what that's about. it seem to show up in the network-manager ok, but couldn't use anything but wep. so that was of no help.

Anyhow - went to the realtek site, grabbed the driver to compile, and i get these errors. after a ./makedrv

I have tried googling this, can't seem to make heads n' tails... anyone got any clues? i'm loosing brain cells. 

Cheers
Grant

ieee80211/
ieee80211/ieee80211_tx.c
ieee80211/Modules.symvers
ieee80211/ieee80211_softmac_wx.c
ieee80211/LICENSE
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_module.c
ieee80211/Makefile
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/ieee80211.h
ieee80211/ieee80211_softmac.c
ieee80211/README
ieee80211/ieee80211_wx.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_crypt.c
rtl818x-0.1/
rtl818x-0.1/r8180_wx.h
rtl818x-0.1/r8180_wx.c
rtl818x-0.1/r8180_rtl8225.h
rtl818x-0.1/r8180_rtl8255.h
rtl818x-0.1/AUTHORS
rtl818x-0.1/r8180_max2820.c
rtl818x-0.1/r8180.h
rtl818x-0.1/r8180_max2820.h
rtl818x-0.1/tags
rtl818x-0.1/r8180_sa2400.h
rtl818x-0.1/r8180_93cx6.c
rtl818x-0.1/ieee80211.h
rtl818x-0.1/r8180_gct.c
rtl818x-0.1/r8180_gct.h
rtl818x-0.1/.r8180_core.o.d
rtl818x-0.1/r8180_rtl8225.c.old
rtl818x-0.1/Modules.symvers
rtl818x-0.1/CHANGES
rtl818x-0.1/LICENSE
rtl818x-0.1/r8180_93cx6.h
rtl818x-0.1/README.master
rtl818x-0.1/r8180_hw.h
rtl818x-0.1/README
rtl818x-0.1/r8180_pm.c
rtl818x-0.1/r8180_sa2400.c
rtl818x-0.1/COPYING
rtl818x-0.1/README.adhoc
rtl818x-0.1/r8180_rtl8225.c
rtl818x-0.1/.tmp_versions/
rtl818x-0.1/.tmp_versions/r8180.mod
rtl818x-0.1/INSTALL
rtl818x-0.1/r8180_rtl8255.c
rtl818x-0.1/r8180_core.c
rtl818x-0.1/r8180_pm.h
rtl818x-0.1/Makefile
rtl818x-0.1/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/grant/rtl8185/ieee80211/tmp
make -C /lib/modules/2.6.20-15-generic/build M=/home/grant/rtl8185/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/grant/rtl8185/ieee80211/ieee80211_softmac.o
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_scan_wq&#8217;:
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:391: warning: ISO C90 forbids mixed declarations and code
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:412: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_stop_scan&#8217;:
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:486: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_associate_abort&#8217;:
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:885: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:1359:4: warning: #warning CHECK_LOCK_HERE
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:1399:2: warning: #warning CHECK_LOCK_HERE
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_rx_frame_softmac&#8217;:
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:1470: warning: ISO C90 forbids mixed declarations and code
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_stop_protocol&#8217;:
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2059: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2167:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2167: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2167: error: (Each undeclared identifier is reported only once
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2167: error: for each function it appears in.)
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2168:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2169:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2170:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2171:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2172:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_free&#8217;:
/home/grant/rtl8185/ieee80211/ieee80211_softmac.c:2191: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
make[2]: *** [/home/grant/rtl8185/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/grant/rtl8185/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/grant/rtl8185/rtl818x-0.1/tmp
make -C /lib/modules/2.6.20-15-generic/build M=/home/grant/rtl8185/rtl818x-0.1 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/grant/rtl8185/rtl818x-0.1/r8180_core.o
In file included from /home/grant/rtl8185/rtl818x-0.1/r8180_core.c:61:
/home/grant/rtl8185/rtl818x-0.1/r8180.h:29:26: error: linux/config.h: No such file or directory
/home/grant/rtl8185/rtl818x-0.1/r8180_core.c:2953:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/grant/rtl8185/rtl818x-0.1/r8180_core.c: In function &#8216;rtl8180_init&#8217;:
/home/grant/rtl8185/rtl818x-0.1/r8180_core.c:2953: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/grant/rtl8185/rtl818x-0.1/r8180_core.c:2953: error: (Each undeclared identifier is reported only once
/home/grant/rtl8185/rtl818x-0.1/r8180_core.c:2953: error: for each function it appears in.)
/home/grant/rtl8185/rtl818x-0.1/r8180_core.c:3276: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/home/grant/rtl8185/rtl818x-0.1/r8180_core.c: In function &#8216;rtl8180_pci_probe&#8217;:
/home/grant/rtl8185/rtl818x-0.1/r8180_core.c:4031: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
make[2]: *** [/home/grant/rtl8185/rtl818x-0.1/r8180_core.o] Error 1
make[1]: *** [_module_/home/grant/rtl8185/rtl818x-0.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

---

### Post by jimmyridge on 2008-02-16
yeah im getting a similar error with my rtl8187 driver on 8.04

  CC [M]  /home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.o
/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.c: In function &#8216;ieee80211_tkip_encrypt_rtl7&#8217;:
/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.c:397: error: &#8216;struct scatterlist&#8217; has no member named &#8216;page&#8217;
/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.c: In function &#8216;ieee80211_tkip_decrypt_rtl7&#8217;:
/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.c:487: error: &#8216;struct scatterlist&#8217; has no member named &#8216;page&#8217;
/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.c: In function &#8216;michael_mic_rtl7&#8217;:
/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.c:547: error: &#8216;struct scatterlist&#8217; has no member named &#8216;page&#8217;
/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.c:551: error: &#8216;struct scatterlist&#8217; has no member named &#8216;page&#8217;
make[3]: *** [/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.o] Error 1
make[2]: *** [_module_/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/james/.sandbox/wifi/rtl/rtl8187_linux_26.1010.0622.2006/ieee80211'
make: *** [all] Error 2

---

### Post by jimmyridge on 2008-02-16
ugh got it to compile/install 

[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

bonus injection patched ;)

---

