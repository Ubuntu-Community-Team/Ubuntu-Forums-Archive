---
title: "Connecting to internet via wireless"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by boaty on 2008-08-07
Yes, I'm new to ubuntu.  Installed it today.  It's amazing.  Anyways. . .

I have no idea what I'm doing.  I've used windows my whole life and hated it.  I'm ready to start something new...but that something new needs to be able to connect to the internet. . .via wireless =].  I'm also a networking noob.  But I do try.  A lot of guides talk as if you have background information on wireless/networking/ubuntu, which I really don't, and thus makes it a bit more difficult

I don't know what info you need.  I guess I'll start out with my computer:
Manufacturer:  Gateway
Model:  MT3422

I installed ubuntu on a ntfs partition using that option on the cd.  There's a story behind why I did that, and it basically involves a cd drive not working properly, so I downloaded ubuntu 8.04 iso and mounted it on a virtual cd drive, giving me access to the install on ntfs/windows option, which I did.

Umm...So yeah.  Thanks to anyone who can help or provide input or keep my spirits up, lol.

---

### Post by chili555 on 2008-08-08
We would like to know the exact details of your wireless card. While booted into Ubuntu, open a terminal (Applications -> Accessories -> Terminal) and type:```
sudo lshw -C network
```One entry will probably be your ethernet adapter and the other your wireless. Post the wireless portion here and we'll help you get it going. If you are in doubt, post both.

---

### Post by boaty on 2008-08-08
```

zach@zach-laptop:~$ sudo lshw -C network
[sudo] password for zach: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
zach@zach-laptop:~$ 

```

That's all it is; is it what you needed to see?

---

### Post by chili555 on 2008-08-08
Yes, that's what I wanted to see. Now I can take 3-4 Xanax and get started. Do you have a working ethernet connection? If so, open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
```Then refer to this: [http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy](http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy)

---

### Post by boaty on 2008-08-08
Thanks, I do have a wired Ethernet connection.  I just installed that thing, and now I'm about to look at the site.  If I have any questions I'll post here, or if I get it to work.

~:Edit:~
Ok, so I went to the site and started working on the commands and after I did ./makedrv and sudo wlan0up.  The instructions said not to worry about warnings, but the wlan0up seemed to come out with weird results.  Is this normal?
```

zach@zach-laptop:~/rtl8185$ ./makedrv
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
patching file ieee80211/ieee80211_crypt_tkip.c
patching file ieee80211/ieee80211_crypt_wep.c
patching file rtl8185/r8180_core.c
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/zach/rtl8185/ieee80211/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/zach/rtl8185/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_softmac.o
/home/zach/rtl8185/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/zach/rtl8185/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/zach/rtl8185/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/zach/rtl8185/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/zach/rtl8185/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/zach/rtl8185/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/zach/rtl8185/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_rx.o
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_tx.o
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_wx.o
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_module.o
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt.o
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.o
/home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_aes_encrypt&#8217;:
/home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:88: warning: passing argument 1 of &#8216;crypto_cipher_encrypt_one&#8217; from incompatible pointer type
/home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_init&#8217;:
/home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:110: warning: assignment from incompatible pointer type
/home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:127: warning: passing argument 1 of &#8216;crypto_free_cipher&#8217; from incompatible pointer type
/home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_deinit&#8217;:
/home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:144: warning: passing argument 1 of &#8216;crypto_free_cipher&#8217; from incompatible pointer type
/home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_set_key&#8217;:
/home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:422: warning: passing argument 1 of &#8216;crypto_cipher_setkey&#8217; from incompatible pointer type
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211-rtl.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/zach/rtl8185/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211-rtl.ko
  CC      /home/zach/rtl8185/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/zach/rtl8185/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/zach/rtl8185/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/zach/rtl8185/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/zach/rtl8185/rtl8185/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/zach/rtl8185/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/zach/rtl8185/rtl8185/r8180_core.o
/home/zach/rtl8185/rtl8185/r8180_core.c: In function &#8216;rtl8180_init&#8217;:
/home/zach/rtl8185/rtl8185/r8180_core.c:3167: warning: assignment from incompatible pointer type
/home/zach/rtl8185/rtl8185/r8180_core.c:3534: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/home/zach/rtl8185/rtl8185/r8180_core.c: At top level:
/home/zach/rtl8185/rtl8185/r8180_core.c:579: warning: &#8216;r8180_get_wireless_stats&#8217; defined but not used
  CC [M]  /home/zach/rtl8185/rtl8185/r8180_sa2400.o
  CC [M]  /home/zach/rtl8185/rtl8185/r8180_93cx6.o
  CC [M]  /home/zach/rtl8185/rtl8185/r8180_wx.o
  CC [M]  /home/zach/rtl8185/rtl8185/r8180_max2820.o
  CC [M]  /home/zach/rtl8185/rtl8185/r8180_gct.o
  CC [M]  /home/zach/rtl8185/rtl8185/r8180_rtl8225.o
  CC [M]  /home/zach/rtl8185/rtl8185/r8180_rtl8225z2.o
  CC [M]  /home/zach/rtl8185/rtl8185/r8180_rtl8255.o
  LD [M]  /home/zach/rtl8185/rtl8185/r8180.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_softmac_stop_protocol_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_wap_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_mode_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_freq_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_rate_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_rate_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_ps_tx_ack" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_freq_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_scan_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_essid_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_mode_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_stop_protocol_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_wap_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_power_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wlan_frequencies_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_power_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_essid_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_start_protocol_rtl" [/home/zach/rtl8185/rtl8185/r8180.ko] undefined!
  CC      /home/zach/rtl8185/rtl8185/r8180.mod.o
  LD [M]  /home/zach/rtl8185/rtl8185/r8180.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
zach@zach-laptop:~/rtl8185$ sudo ./wlan0up
zach@zach-laptop:~/rtl8185$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211-rtl.ko': -1 File exists
insmod: error inserting 'r8180.ko': -1 File exists


```


Also, now I'm on [http://www.willdaniels.co.uk/articles/howto-guides/10-howto/10-wpa-r8180-ubuntu](http://www.willdaniels.co.uk/articles/howto-guides/10-howto/10-wpa-r8180-ubuntu) for my WEP.  Is this where I need to go?

Thanks for all you help =]

---

### Post by boaty on 2008-08-08
First, sorry for double post, usually a bad idea in fora, but I'm excited now.  My wireless works.  I don't know how, or what or where, but you definitely got me started, and I started tinkering around, downloaded some programs to see what I could get and lo and behold, here I am.  For now at least.  I may have to come back with some weird reason that it doesn't work tomorrow, lol.

Thanks!!!

---

