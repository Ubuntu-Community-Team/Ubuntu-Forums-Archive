---
title: "Belkin f5d7000 v7 RTL8185L Problems..."
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by Mr_Pag on 2008-05-10
Hello Forum,

Every time a new Ubuntu is released I install it on my main desktop and have a good  play around with it to see what I can do. I am extremely impressed with 8.04 32bit, my USB sound card now appears to work quite seamlessly (prob due to pulseaudio)and Wubi has allowed me to install the software for evaluation without screwing up partition tables etc.

One problem still remains – the RTL8185L based WLAN card still refuses to work. After installation of the Win98 driver with the  ndiswrapper GTK front end I have gotten so far -

The list of networks in the area show up and all the signal strengths appear to be relative to the ones acquired with XP's zero config. Those that are secured show up as such, although connection to any network regardless of security type is impossible.

 I've had a good trawl of the forums for a fix and people are going a bit banana's trying to get this one going. 

It's a Belkin f5d7000 v7, and most people have taken one of three routes to get the thing going -

* Installed ndiswrapper and tried the Belkin drivers, some people have had success with the Windows 98/ME version. I can't connect as described above.
* Attempted to modify the RTL8185L driver by associating it with the Belkin PCI ID, and install that with ndiswrapper.
* Attempted to compile the open source driver on RTKs website, I haven't had much luck with this either, with the compile bombing out shortly after -

```
home/pag/rtk/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/pag/rtk/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/pag/rtk/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/pag/rtk/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/pag/rtk/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/pag/rtk/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/pag/rtk/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]
```

I've heard this used to compile on older kernels?

Does anyone have any suggestions? Is there a second chip on the card not commonly associated with the RTK part? I bet there's a few people on these forums would send you a mars bar for working this one out. I will ship 1st class :D

---

Unrelated, but it was a real PITA to install this thing under Vista x64 as well. The official Belkin driver didn't work (and probably still doesn't). The one from windows update (released a good couple of months after I bought the card) did...

---

### Post by Mr_Pag on 2008-05-11
Fixed It. I don't know how though...

Ended up using a "vanilla" Realtek 8185 INF and associating it with the Belkin card. This has never worked in the past (from about 6.10 upwards) so I don't see why it should do it now. 

I wish I could say I took a definitive step to getting it to work but it seemed to magically "click" after a frustrating period of refusing to take an IP address off the router via DHCP. Just kept typing in the WEP key and waiting... sixth try or so I got a successful connect :confused:

Connection seems pretty consistent and hasn't dropped at all yet, which is more than I can say for the windows side of the machine :D

I can help anyone then I'll do my best.

---

