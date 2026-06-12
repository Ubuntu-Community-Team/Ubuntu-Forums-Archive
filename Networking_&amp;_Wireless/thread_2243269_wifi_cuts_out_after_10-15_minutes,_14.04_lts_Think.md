---
title: "wifi cuts out after 10-15 minutes, 14.04 lts ThinkPad Edge"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by samdrake2010 on 2014-09-07
Hey guys, wifi will cut out and refuse to reconnect after maye 10-15 minutes from a reboot. Rebooting normally fixes it temporarily. I'm not sure what outputs would be helpful as a starting point so just let me know what you need and I'll grab it.

---

### Post by praseodym on 2014-09-07
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by tgalati4 on 2014-09-08
I could simply be wireless congestion:

tgalati4@Mint14-Extensa ~ $ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Galati Slow Lane"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:B5:34:C9:82   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          **Link Quality=65/70  Signal level=-45 dBm ** 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:247   Missed beacon:0

If you are getting excessive errors or if your signal level is too low (below -70 dBm, typical noise level is -93 or -94 dBm), then you may have problems.  Try rebooting the wireless router and reseating the internet connection to it.

If you have an Android phone, install *WiFi Analyzer* and use that to see how bad your wireless network is.    Antenna placement and channel selection is critical to consistent wifi performance.

In linux, you can use *wifi-radar* to see your neighboring networks and identify sources of interference.

---

