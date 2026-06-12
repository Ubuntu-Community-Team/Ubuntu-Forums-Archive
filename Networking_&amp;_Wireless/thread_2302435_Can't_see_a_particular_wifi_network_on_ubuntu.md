---
title: "Can't see a particular wifi network on ubuntu"
date: 2015-11-10
forum: Networking &amp; Wireless
---

### Post by cihan4 on 2015-11-10
[FONT=Helvetica Neue]I cant see my wifi network. i see all available networks except mine. i was using it always but last night i connected another wifi network and i couldnt see my own wifi anymore.[/FONT]
[h=1]ifconfig[/h]wlan0     Link encap:Ethernet  HWaddr 4c:0f:6e:90:3b:a1  
  UP BROADCAST MULTICAST  MTU:1500  Metric:1
  RX packets:3423 errors:0 dropped:0 overruns:0 frame:0
  TX packets:3181 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0 txqueuelen:1000 
  RX bytes:2369381 (2.3 MB)  TX bytes:570573 (570.5 KB)
[h=1]iwconfig[/h]wlan0     IEEE 802.11bgn  ESSID:off/any  
  Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
  Retry short limit:7   RTS thr:off   Fragment thr:off
  Power Management:off
[FONT=Helvetica Neue]I am trying to connect a 802.1x wifi[/FONT]
[FONT=Helvetica Neue]Thanks for help[/FONT]

---

### Post by SeijiSensei on 2015-11-10
Do you have your router configured to advertise the SSID?  That's usually the default, but maybe you turned it off?

---

### Post by cihan4 on 2015-11-11
I have windows os too. It sees the network and other pcs can see too. Only my ubuntu doesnt. I checked with airodump-ng and the network in my stations and out of range

---

### Post by SeijiSensei on 2015-11-11
Try running "sudo iwlist scan" from a command prompt.  Does it show up there?

---

### Post by cihan4 on 2015-11-11
No, not there. i will format now then try again. this situation driving me crazy

---

