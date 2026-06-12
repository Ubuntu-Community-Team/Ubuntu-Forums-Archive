---
title: "wireless connects but n ointernet"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by morganGDFP on 2007-03-04
Hello again. 
I am having new wireless problems..
I can connect to my Speed Touch Wireless ADSL gateway, with poor connection quality (24%) but that's all i can do. no Internet, Email, or messenger. I can't even access the SpeedTouch configuration page.

Is it because I have such a bad signal that I can't access Internet or could the problem be of some other kind?

The problem started when I removed a linksys wireless router that was sitting between my SpeedTouch wireless modem and my home network.
I had some problems accessing shared files and the printer since I had some computers on a sub network from the wifi router and some on the actual network.

Here is my setup now:
A speedTouch 585 Wireless Residential ADSL Gateway that connects to the internet and three computers (two running winXP and mine running ubuntu 6.10) connecting to the through wireless. in my ubuntu machine i have a D-Link AirPlus DWL-G520 Wireless PCI adapter.

and running lspci gives me this:
```
00:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

and iwconfig:

```
ath0      IEEE 802.11g  ESSID:"SpeedTouch9FE8F0"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:7F:24:73:7B   
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/94  Signal level=-71 dBm  Noise level=-95
```

I dual boot with windows and I can access internet on windows..
Please help.

---

### Post by morganGDFP on 2007-03-04
Now it's getting weirder still..
I play around with the Gnome network manager applet and now I can connect to my wireless network but if I try to connect to the wired one I get the same symptom as i did before..
I says that it's connected but I can't access internet or anything...

Actually I'm happy as long as the wireless is working, but my guess is that it's going to stop soon..

I guess I'll just wait and see what happens...

---

### Post by ragespot on 2007-03-07
try to enter in ubuntu your dns setting, I already got this problem. your ISP should provide this information.

---

