---
title: "[SOLVED] wireless problem with Broadcom  BCM94311MCG wlan mini-PCI [14e4:4311] (rev 0"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by harshaambati on 2008-06-30
I was successfully able to use wireless on my Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02) with fix from 
[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html") (From dmizer) 
until lately i don't see any wireless networks available to connect
i pretty much don't know what i was doing wrong or what i did do to screw up the wireless....but i see that my card was being recognized in the restricted drivers (or hardware drivers) list it was not there before ( i mean before it didn't even recognize my broadcom driver as restricted driver..i had to use the fix above... i think maybe its because of the updates, the driver suddenly show up in restricted drivers.. i removed the wireless fix and ndiswrapper..and enabled the hardware driver (restricted driver) for wireless( i.e. installed b43-fwcutter).. surprisingly it recognizes my wireless devices..but doesn't show any wireless networks for me to connect to...

Can any one help me....

here is what i get for $ iwconfig

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ sudo iwlist wlan0 scan
wlan0     No scan results

---

