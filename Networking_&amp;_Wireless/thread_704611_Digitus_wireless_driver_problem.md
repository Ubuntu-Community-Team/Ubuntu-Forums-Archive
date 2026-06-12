---
title: "Digitus wireless driver problem"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by DaveEngland on 2008-02-22
I am using a Digitus wireless card, and ubuntu doesnt recognize the card.
I have this card:
  [http://www.digitus.info/scripts/digdetail.asp?artnr=DN%2D7006GS](http://www.digitus.info/scripts/digdetail.asp?artnr=DN%2D7006GS)

If I type lspci I get this:
00:0b.0 Ethernet controller. Marvel technology group Ltd. 88w335 [Libertas] 802.11b/g wireless (rev. 03)
I have allready tryed with ndiswrapper & windows drivers, but i cant get it to recognize the card!
I need urgent help!

---

### Post by jeffus_il on 2008-02-22
It uses a Realtek Chip (Realtek-Chipsatz) so you need to load one of the rtxxxx modules. Will try to find out which one and get back soon ...

---

### Post by DaveEngland on 2008-02-22
yes,please help!

---

### Post by jeffus_il on 2008-02-22
There is a Linux driver on their site. Click on the download button and you will see it, it uses the RTL8185 chip. It also has an English manual to download. You may have a suitable driver on your system. Try: > lsmod | grep rtl
to see if you have Realtek modules loaded. Also do > iwconfig
in a terminal and post the output here.

---

### Post by DaveEngland on 2008-02-22
This is the entire process!
I have tryed to install the driver from the page!

dave@dave-desktop:~/DN$ ./makedrv
bash: ./makedrv: Permission denied
dave@dave-desktop:~/DN$ chmod u+x makedrv
dave@dave-desktop:~/DN$ ./makedrv
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
rm -rf /home/dave/DN/ieee80211/tmp
make -C /lib/modules/2.6.22-14-generic/build M=/home/dave/DN/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/dave/DN/ieee80211/ieee80211_softmac.o
/home/dave/DN/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/dave/DN/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/dave/DN/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/dave/DN/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/dave/DN/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/dave/DN/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/dave/DN/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]  /home/dave/DN/ieee80211/ieee80211_rx.o
  CC [M]  /home/dave/DN/ieee80211/ieee80211_tx.o
  CC [M]  /home/dave/DN/ieee80211/ieee80211_wx.o
  CC [M]  /home/dave/DN/ieee80211/ieee80211_module.o
  CC [M]  /home/dave/DN/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/dave/DN/ieee80211/ieee80211_crypt.o
  CC [M]  /home/dave/DN/ieee80211/ieee80211_crypt_ccmp.o
/home/dave/DN/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_aes_encrypt&#8217;:
/home/dave/DN/ieee80211/ieee80211_crypt_ccmp.c:88: warning: passing argument 1 of &#8216;crypto_cipher_encrypt_one&#8217; from incompatible pointer type
/home/dave/DN/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_init&#8217;:
/home/dave/DN/ieee80211/ieee80211_crypt_ccmp.c:110: warning: assignment from incompatible pointer type
/home/dave/DN/ieee80211/ieee80211_crypt_ccmp.c:127: warning: passing argument 1 of &#8216;crypto_free_cipher&#8217; from incompatible pointer type
/home/dave/DN/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_deinit&#8217;:
/home/dave/DN/ieee80211/ieee80211_crypt_ccmp.c:144: warning: passing argument 1 of &#8216;crypto_free_cipher&#8217; from incompatible pointer type
/home/dave/DN/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_set_key&#8217;:
/home/dave/DN/ieee80211/ieee80211_crypt_ccmp.c:422: warning: passing argument 1 of &#8216;crypto_cipher_setkey&#8217; from incompatible pointer type
  CC [M]  /home/dave/DN/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/dave/DN/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211-rtl.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/dave/DN/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211-rtl.ko
  CC      /home/dave/DN/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/dave/DN/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/dave/DN/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/dave/DN/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/dave/DN/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/dave/DN/rtl8185/tmp
make -C /lib/modules/2.6.22-14-generic/build M=/home/dave/DN/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/dave/DN/rtl8185/r8180_core.o
/home/dave/DN/rtl8185/r8180_core.c: In function &#8216;rtl8180_init&#8217;:
/home/dave/DN/rtl8185/r8180_core.c:3159: warning: assignment from incompatible pointer type
/home/dave/DN/rtl8185/r8180_core.c:3522: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
/home/dave/DN/rtl8185/r8180_core.c:3522: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/home/dave/DN/rtl8185/r8180_core.c: At top level:
/home/dave/DN/rtl8185/r8180_core.c:579: warning: &#8216;r8180_get_wireless_stats&#8217; defined but not used
  CC [M]  /home/dave/DN/rtl8185/r8180_sa2400.o
  CC [M]  /home/dave/DN/rtl8185/r8180_93cx6.o
  CC [M]  /home/dave/DN/rtl8185/r8180_wx.o
  CC [M]  /home/dave/DN/rtl8185/r8180_max2820.o
  CC [M]  /home/dave/DN/rtl8185/r8180_gct.o
  CC [M]  /home/dave/DN/rtl8185/r8180_rtl8225.o
  CC [M]  /home/dave/DN/rtl8185/r8180_rtl8225z2.o
  CC [M]  /home/dave/DN/rtl8185/r8180_rtl8255.o
  LD [M]  /home/dave/DN/rtl8185/r8180.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_softmac_stop_protocol_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_wap_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_mode_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_freq_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_rate_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_rate_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_ps_tx_ack" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_freq_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_scan_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_essid_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_mode_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_stop_protocol_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_wap_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_power_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wlan_frequencies_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_power_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_essid_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_start_protocol_rtl" [/home/dave/DN/rtl8185/r8180.ko] undefined!
  CC      /home/dave/DN/rtl8185/r8180.mod.o
  LD [M]  /home/dave/DN/rtl8185/r8180.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'


dave@dave-desktop:~/DN$ ./wlan0up
bash: ./wlan0up: Permission denied
dave@dave-desktop:~/DN$ chmod u+x wlan0up
dave@dave-desktop:~/DN$ ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8180.ko': -1 Operation not permitted
wlan0: ERROR while getting interface flags: No such device
dave@dave-desktop:~/DN$ 


What is wrong here???

---

### Post by DaveEngland on 2008-02-23
still need some help :(

---

### Post by DaveEngland on 2008-02-23
please try to help.. i need to have the drivers as much as possible!

---

### Post by jeffus_il on 2008-02-23
You need to do>  sudo ./wlan0up in your last step, you need root privileges to run "insmod"

---

