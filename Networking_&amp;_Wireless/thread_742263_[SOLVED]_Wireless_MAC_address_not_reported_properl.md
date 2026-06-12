---
title: "[SOLVED] Wireless MAC address not reported properly"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by eiceak14 on 2008-04-01
I have a 5008 Atheros based wireless card from Dlink and my MAC address is being reported differently based upon what command I use.  It's causing problems for me when I try to associate with my AP.

ifconfig reports:
ath1      Link encap:Ethernet  HWaddr 06:19:5B:09:36:14  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-5B-09-36-14-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12261 errors:0 dropped:124 overruns:0 frame:677
          TX packets:2363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:2325330 (2.2 MB)  TX bytes:109670 (107.0 KB)
          Interrupt:18 

why is one address being listed with a "06" while the other shows "00"

the correct one should be "00" .. and when i have the card in monitor mode.. and try to associate with an ap using airplay-ng - it says that my card's address is different than the address i use in the -h parameter of the command.  the command is typed in properly, but the only difference i see is once again that the card's mac address is being reported differently from what it REALLY is.  

Can you help?

---

### Post by eiceak14 on 2008-04-04
Found the problem, just need to use the 'bssid' flag option in the wlanconfig command while creating the device.  This forces the VAP to use the same MAC address as the underlying device.

---

