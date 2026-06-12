---
title: "Compile Driver issues"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by Highspade on 2008-03-16
Hello, I'm trying to compile my wireless driver for a realtek 8185L I downloaded the latest one from the realtek site and I am getting these errors when following the readme. Could anyone point me in the right direction here? (I would like to add that I get errors when trying to compile ndiswrapper as well so I assume that something is messed up, or I am missing some essential items) 

iroy@kbunt:~/dl/8185$ sudo ./makedrv
./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko
rm -rf /home/iroy/dl/8185/ieee80211/tmp
make -C /lib/modules/2.6.24-11-generic/build M=/home/iroy/dl/8185/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-11-generic'
  CC [M]  /home/iroy/dl/8185/ieee80211/ieee80211_softmac.o
/home/iroy/dl/8185/ieee80211/ieee80211_softmac.c: In function âieee80211_softmac_initâ:
/home/iroy/dl/8185/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/iroy/dl/8185/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/iroy/dl/8185/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/iroy/dl/8185/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/iroy/dl/8185/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/iroy/dl/8185/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]  /home/iroy/dl/8185/ieee80211/ieee80211_rx.o
  CC [M]  /home/iroy/dl/8185/ieee80211/ieee80211_tx.o
  CC [M]  /home/iroy/dl/8185/ieee80211/ieee80211_wx.o
  CC [M]  /home/iroy/dl/8185/ieee80211/ieee80211_module.o
  CC [M]  /home/iroy/dl/8185/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/iroy/dl/8185/ieee80211/ieee80211_crypt.o
  CC [M]  /home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.o
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.c: In function âieee80211_ccmp_aes_encryptâ:
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.c:88: warning: passing argument 1 of âcrypto_cipher_encrypt_oneâ                                           from incompatible pointer type
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.c: In function âieee80211_ccmp_initâ:
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.c:110: warning: assignment from incompatible pointer type
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.c:127: warning: passing argument 1 of âcrypto_free_cipherâ from i                                          ncompatible pointer type
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.c: In function âieee80211_ccmp_deinitâ:
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.c:144: warning: passing argument 1 of âcrypto_free_cipherâ from i                                          ncompatible pointer type
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.c: In function âieee80211_ccmp_set_keyâ:
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_ccmp.c:422: warning: passing argument 1 of âcrypto_cipher_setkeyâ from                                           incompatible pointer type
  CC [M]  /home/iroy/dl/8185/ieee80211/ieee80211_crypt_tkip.o
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_tkip.c: In function âieee80211_tkip_encryptâ:
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_tkip.c:417: error: âstruct scatterlistâ has no member named âpageâ
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_tkip.c: In function âieee80211_tkip_decryptâ:
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_tkip.c:511: error: âstruct scatterlistâ has no member named âpageâ
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_tkip.c: In function âmichael_micâ:
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_tkip.c:613: error: âstruct scatterlistâ has no member named âpageâ
/home/iroy/dl/8185/ieee80211/ieee80211_crypt_tkip.c:617: error: âstruct scatterlistâ has no member named âpageâ
make[2]: *** [/home/iroy/dl/8185/ieee80211/ieee80211_crypt_tkip.o] Error 1
make[1]: *** [_module_/home/iroy/dl/8185/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-11-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/iroy/dl/8185/rtl8185/tmp
make -C /lib/modules/2.6.24-11-generic/build M=/home/iroy/dl/8185/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-11-generic'
  CC [M]  /home/iroy/dl/8185/rtl8185/r8180_core.o
/home/iroy/dl/8185/rtl8185/r8180_core.c: In function ârtl8180_proc_module_initâ:
/home/iroy/dl/8185/rtl8185/r8180_core.c:588: error: âproc_netâ undeclared (first use in this function)
/home/iroy/dl/8185/rtl8185/r8180_core.c:588: error: (Each undeclared identifier is reported only once
/home/iroy/dl/8185/rtl8185/r8180_core.c:588: error: for each function it appears in.)
/home/iroy/dl/8185/rtl8185/r8180_core.c: In function ârtl8180_proc_module_removeâ:
/home/iroy/dl/8185/rtl8185/r8180_core.c:594: error: âproc_netâ undeclared (first use in this function)
/home/iroy/dl/8185/rtl8185/r8180_core.c: In function ârtl8180_initâ:
/home/iroy/dl/8185/rtl8185/r8180_core.c:3159: warning: assignment from incompatible pointer type
/home/iroy/dl/8185/rtl8185/r8180_core.c:3522: error: âSA_SHIRQâ undeclared (first use in this function)
/home/iroy/dl/8185/rtl8185/r8180_core.c:3522: warning: passing argument 2 of ârequest_irqâ from incompatible pointe                                          r type
/home/iroy/dl/8185/rtl8185/r8180_core.c: In function ârtl8180_pci_probeâ:
/home/iroy/dl/8185/rtl8185/r8180_core.c:4213: error: implicit declaration of function âSET_MODULE_OWNERâ
make[2]: *** [/home/iroy/dl/8185/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/iroy/dl/8185/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-11-generic'
make: *** [modules] Error 2
iroy@kbunt:~/dl/8185$

---

### Post by Sef on 2008-03-16
Moved to Networking and Wireless.

---

