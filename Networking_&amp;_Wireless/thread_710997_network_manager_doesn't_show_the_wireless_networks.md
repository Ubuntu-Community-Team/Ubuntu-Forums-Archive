---
title: "network manager doesn't show the wireless networks"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by einsn on 2008-02-29
I plugged  in VIA wireless adapter (VT6656) on ubuntu 7.10, loaded the driver and run it manually in a terminal, then clicked the network manager icon, but network manager doesn't show the wireless networks window even if VT6656 had connected an AP.

but when another Ralink Wireless Card plug in, it showed the wireless networks window, captured as follow:

[IMG]http://forum.ubuntu.org.cn/download.php?id=28589[/IMG]

anyone tell me why?Thanks!

---

### Post by Hightide on 2008-02-29
Hi einsn

You  may find Kevdog's wireless [tutorial ]("http://ubuntuforums.org/showthread.php?t=571194")useful


regards

:)

---

### Post by einsn on 2008-03-02
Thanks Hightide, but I am implementing  VT6656  to support the network manager completely.

And I found the Ralink wireless used more than one driver module. 

modules related to it:
rc80211_simple          6912  1 
rt73usb                25344  0 
rt2x00usb              12032  1 rt73usb
rt2x00lib              19584  2 rt73usb,rt2x00usb
rfkill                  8208  1 rt2x00lib
mac80211              171016  3 rc80211_simple,rt2x00usb,rt2x00lib
cfg80211                7304  1 mac80211
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib

there is an abstract about the mac80211

mac80211 is the Linux stack for 802.11 hardware that implements only partial functionality in hard- or firmware. This document defines the interface between mac80211 and low-level hardware drivers.

I get a supported  driver list of mac80211:

mac80211 drivers
Here is a list of current mac80211 drivers:
      adm8211
      ath5k
      b43
      b43legacy
      iwl3945
      iwl4965
      ub8xxx
      p54_pci
      p54_usb
      rt2400pci
      rt2500pci
      rt2500usb
      rt61pci
      rt73usb
      rtl8180
      rtl8187
      zd1211rw-mac80211 

Does it mean that others drivers not support  the mac80211?
Does the behavior(whether it showed the wireless network or not) of network manager decide  by  mac80211?

---

