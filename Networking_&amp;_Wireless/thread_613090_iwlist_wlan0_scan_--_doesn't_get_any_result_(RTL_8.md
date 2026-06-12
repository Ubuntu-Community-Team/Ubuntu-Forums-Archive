---
title: "iwlist wlan0 scan -- doesn't get any result (RTL 8185)"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by coriamauricio on 2007-11-14
Hello guys,

I've installed ubuntu 7.10, and my linux box has a (RTL 8185) wich ubuntu detects correctly (I think).

r# lspci
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

my module is loaded...

ieee80211_crypt_ccmp     8064  0
ieee80211_crypt_tkip    11776  0
ieee80211_crypt_wep     6272  0
ieee80211_crypt         7040  3 ieee80211_crypt_ccmp,ieee80211_crypt_tkip,ieee80211_crypt_wep
r8180                  89868  0
ieee80211_rtl          80520  1 r8180

however I can't list or acces my wireless network 

# ifconfig wlan0 up
# iwlist wlan0 scan
wlan0     No scan results

any idea about this problem?

I will appreciate.

Thanks,
Mauricio

---

### Post by jackocleebrown on 2007-12-09
I have the same problem (ndiswrapper with neti2220) scan does not work on boot - I can connect to a accesspoint if I know the name and once any wifi connection has been made everything works fine (i.e. scan suddenly does work)

Have been looking around for an answer. Nothing yet but it seems we are not alone:

[http://ubuntuforums.org/showthread.php?t=593696](http://ubuntuforums.org/showthread.php?t=593696)
[http://ubuntuforums.org/showthread.php?t=587971](http://ubuntuforums.org/showthread.php?t=587971)

---

