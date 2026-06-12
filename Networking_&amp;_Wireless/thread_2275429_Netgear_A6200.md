---
title: "Netgear A6200"
date: 2015-04-26
forum: Networking &amp; Wireless
---

### Post by thibaut-caritey on 2015-04-26
Hello, 


I have a netgear a6200 wireless adapter.


I installed the driver:


```
  ti-san@tisan ~ $ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (0846:9050) present
  
```


When I connect to my router, I cant have access to internet: the ping command doesnt give back any result.
```
ti-san@tisan ~ $ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
```






Also, the card is working with 802.11 g, n, ac standard but only the 802.11 g standard seems activated. I can only scan the 2.4 Ghz network and no 5 Ghz ones.


```
ti-san@tisan ~ $ iwconfig wlan1
wlan1     IEEE 802.11g  ESSID:"dlink-872B"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: C8:D3:A3:6B:87:2B   
          Bit Rate=130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:432  Invalid misc:613808   Missed beacon:0
``````

```




What is the issue ? Is the driver faulty ?


Thank you in advance.

---

