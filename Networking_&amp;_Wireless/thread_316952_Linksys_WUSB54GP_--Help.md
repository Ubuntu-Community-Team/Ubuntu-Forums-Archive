---
title: "Linksys WUSB54GP --Help"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by 200mg on 2006-12-11
I have a usb wireless card I can't get to work.  It shows under lsusb

```
root@trace:/home/trace/Desktop# lsusb
Bus 004 Device 005: ID 5041:2235 Linksys (?)
```

it shows under iwconfig

```
root@trace:/home/trace/Desktop# iwconfig eth2
eth2      IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I am guessing this is the driver it's using.

```
root@trace:/home/trace/Desktop# lsmod|grep 80211
ieee80211softmac       33792  1 islsm
ieee80211              35272  2 islsm,ieee80211softmac
ieee80211_crypt         7552  1 ieee80211
```

Now I know I am next to a wlan because the AP is 20 feet outside my door, and my laptop with winXP can pick it up, but I get this.

```
root@trace:/home/trace/Desktop# iwlist eth2 scan
eth2      No scan results
root@trace:/home/trace/Desktop# 
```

Why doesn't this work?  Brand new card out of the box.  I have heard it's "well supported" but I cannot get it to work.  Any ideas?

---

