---
title: "Feisty wireless using 2.6.17.11"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by glendavee on 2007-04-29
I have just upgraded from 6.10 to 7.04. Everything seems fine, except that I have no wireless connection. When I check using   "sudo ndiswrapper -l" my device is present. When I reboot in kernel 2.6.17.11 instead of 2.6.20.15 my connection is restored and everything seems fine.
My question is, "is there any reason why I shouldn't continue to run 7.04 using the old kernel (2.6.17.11)?

---

### Post by wagdog on 2007-04-30
Bump for the same problem - except I have to go back to 2.6.15 before my wireless works again.

---

### Post by glendavee on 2007-04-30
More info - don't know if this is significant. In 2.6.17.11 Network Manager shows 3 possible network connections, and output from iwconfig is :
[COLOR="Red"]lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:"hol5mes"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:30:F1:E9:DC:70   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off 
          Link Quality:81/100  Signal level:-44 dBm  Noise level:-96 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

sit0      no wireless extensions. [/COLOR]

In 2.6.20.15 Network Manager shows an extra connection - wmaster0, and iwconfig gives :

[COLOR="Red"]lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  IEEE 802.11g  Frequency:2.462 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"hol5mes"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:30:F1:E9:DC:70   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 [/COLOR]

Is it possible that the connection "wmaster0" is the problem? If so, how do I get rid of it?

Just to repeat, wireless works fine under 2.6.17.11, but not under 2.6.20.15???????

---

### Post by glendavee on 2007-05-08
Discovered that if the USB wireless card is unplugged whilst booting, then plugged in, wireless works fine with kernel 2.6.20.15, using Wicd as network manager. Don't know why, though?

---

