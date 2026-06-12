---
title: "Driver installation fails, should be easy for you guys"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by then00b on 2008-11-06
I have tried this in Backtrack 3 boot cd, and in the latest Ubuntu which I am on right now.

So I have a realtek 8185 chipset PCI wifi card, snatch the drivers from teh net.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352)

Download, extract the files, look at the readme, go to the installation portion, says get your terminal and go ./makedrv, so I do so.
```
john@john-desktop:~$ su
Password: 
root@john-desktop:/home/john# cd Desktop
root@john-desktop:/home/john/Desktop# cd 8185
root@john-desktop:/home/john/Desktop/8185# ./makedrv
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
rm -rf /home/john/Desktop/8185/ieee80211/tmp
make -C /lib/modules/2.6.24-21-generic/build M=/home/john/Desktop/8185/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/john/Desktop/8185/ieee80211/ieee80211_softmac.o
/home/john/Desktop/8185/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/john/Desktop/8185/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/john/Desktop/8185/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/john/Desktop/8185/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/john/Desktop/8185/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/john/Desktop/8185/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/john/Desktop/8185/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]  /home/john/Desktop/8185/ieee80211/ieee80211_rx.o
  CC [M]  /home/john/Desktop/8185/ieee80211/ieee80211_tx.o
  CC [M]  /home/john/Desktop/8185/ieee80211/ieee80211_wx.o
  CC [M]  /home/john/Desktop/8185/ieee80211/ieee80211_module.o
  CC [M]  /home/john/Desktop/8185/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/john/Desktop/8185/ieee80211/ieee80211_crypt.o
  CC [M]  /home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.o
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.c:88: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.c:110: warning: assignment from incompatible pointer type
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.c:127: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.c:144: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_ccmp.c:422: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/john/Desktop/8185/ieee80211/ieee80211_crypt_tkip.o
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_tkip.c: In function ‘ieee80211_tkip_encrypt’:
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_tkip.c:417: error: ‘struct scatterlist’ has no member named ‘page’
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_tkip.c: In function ‘ieee80211_tkip_decrypt’:
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_tkip.c:511: error: ‘struct scatterlist’ has no member named ‘page’
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_tkip.c: In function ‘michael_mic’:
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_tkip.c:613: error: ‘struct scatterlist’ has no member named ‘page’
/home/john/Desktop/8185/ieee80211/ieee80211_crypt_tkip.c:617: error: ‘struct scatterlist’ has no member named ‘page’
make[2]: *** [/home/john/Desktop/8185/ieee80211/ieee80211_crypt_tkip.o] Error 1
make[1]: *** [_module_/home/john/Desktop/8185/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/john/Desktop/8185/rtl8185/tmp
make -C /lib/modules/2.6.24-21-generic/build M=/home/john/Desktop/8185/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/john/Desktop/8185/rtl8185/r8180_core.o
/home/john/Desktop/8185/rtl8185/r8180_core.c: In function ‘rtl8180_proc_module_init’:
/home/john/Desktop/8185/rtl8185/r8180_core.c:588: error: ‘proc_net’ undeclared (first use in this function)
/home/john/Desktop/8185/rtl8185/r8180_core.c:588: error: (Each undeclared identifier is reported only once
/home/john/Desktop/8185/rtl8185/r8180_core.c:588: error: for each function it appears in.)
/home/john/Desktop/8185/rtl8185/r8180_core.c: In function ‘rtl8180_proc_module_remove’:
/home/john/Desktop/8185/rtl8185/r8180_core.c:594: error: ‘proc_net’ undeclared (first use in this function)
/home/john/Desktop/8185/rtl8185/r8180_core.c: In function ‘rtl8180_init’:
/home/john/Desktop/8185/rtl8185/r8180_core.c:3159: warning: assignment from incompatible pointer type
/home/john/Desktop/8185/rtl8185/r8180_core.c:3522: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/john/Desktop/8185/rtl8185/r8180_core.c:3522: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/john/Desktop/8185/rtl8185/r8180_core.c: In function ‘rtl8180_pci_probe’:
/home/john/Desktop/8185/rtl8185/r8180_core.c:4213: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: *** [/home/john/Desktop/8185/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/john/Desktop/8185/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [modules] Error 2
root@john-desktop:/home/john/Desktop/8185# ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8180.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device
root@john-desktop:/home/john/Desktop/8185# 
root@john-desktop:/home/john/Desktop/8185# 

```

So obviously this is an issue and I don't know how to rectify it.

Thanks!

---

### Post by Aarookie on 2008-11-07
try this
Open a terminal and enter these commands:
(this is also assuming like me the target computer has no way of getting to the internet, if you have RJ45 plugged in or some alternate method of connecting to internet you can skip first step.

1. Insert your Ubuntu cd and open terminal
2.sudo apt-cdrom add
3.sudo apt-get install build-essential (Not sure this part is necessary but it sure was for proper tarballing when I was trying to install multiple tar.gz files.
4.sudo apt-get install ndisgtk

5.Open system>administration>Windows wireless drivers menu/program.
6.My computer sort of stuttered at this point but eventually a little window opened up and I was able to browse to my .inf file from winxp driver.
7.For some reason configure network didn't work at this point the unlock button was greyed out, also mouse pointer was skipping a few beats every so often but after a restart I am able to click on my 2 little computers in the gnome task bar and attempt to connect to my network same way I have done on my laptop here. At this point however I was unable to connect to wpa type network, switched router back to wep and hooked right up

---

