---
title: "WiFi Adpater not found in Ubuntu 18.10 on Samsung Galaxy Book 10.6"
date: 2018-11-12
forum: Networking &amp; Wireless
---

### Post by testing990 on 2018-11-12
Hello, I have connected my 

Samsung Galaxy Book 10.6 with a Ubuntu 18.10 installation over
a tethered phone to the internet,

as the Galaxy Book's Wifi is not working.
The Network manager shows "no wifi adapter found".

The Diagnostics File I have posted here via pastebin:

[https://paste.ubuntu.com/p/P8CDXbb3Rr/](https://paste.ubuntu.com/p/P8CDXbb3Rr/)


For the Galaxy book 12 in combination with Ubuntu 17.10
a fix as described here seems to have worked:

[https://ubuntuforums.org/showthread.php?t=2384640](https://ubuntuforums.org/showthread.php?t=2384640)

Furthermore, no sound (only via bluetooth) and no camera works.
Anyhow, I do get this error, both on the git for the 4.16 and 4.17 kernel. how can i fix this?

(the incompatible pointer type points to the = symbol)

~/atheros$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
make: Entering directory '/usr/src/linux-headers-4.18.0-10-generic'
  CC [M]  /home/computer/atheros/ath9k/main.o
/home/computer/atheros/ath9k/main.c: In function &#8216;ath9k_fill_chanctx_ops&#8217;:
/home/computer/atheros/ath9k/main.c:2635:37: error: assignment to &#8216;void  (*)(struct ieee80211_hw *, struct ieee80211_vif *, u16)&#8217; {aka &#8216;void  (*)(struct ieee80211_hw *, struct ieee80211_vif *, short unsigned int)&#8217;}  from incompatible pointer type &#8216;void (*)(struct ieee80211_hw *, struct  ieee80211_vif *)&#8217; [-Werror=incompatible-pointer-types]
  ath9k_ops.mgd_prepare_tx           = ath9k_mgd_prepare_tx;
                                     ^
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:327: /home/computer/atheros/ath9k/main.o] Error 1
make[1]: *** [scripts/Makefile.build:581: /home/computer/atheros/ath9k] Error 2
make: *** [Makefile:1546: _module_/home/computer/atheros] Error 2
make: Leaving directory '/usr/src/linux-headers-4.18.0-10-generic'
computer@computer:~/atheros$


Thank you for your help!

---

### Post by testing990 on 2018-11-19
anyone?

---

