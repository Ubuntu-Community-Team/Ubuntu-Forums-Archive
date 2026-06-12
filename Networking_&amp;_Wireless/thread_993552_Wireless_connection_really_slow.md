---
title: "Wireless connection really slow"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by dvkris on 2008-11-25
I had recently installed Ubuntu 8.04...
I'm using a Dell GX260
2.24 GHz
750 MB DDR Ram
64 MB video
Linksys Wireless-G USB Adapter (WUSB54G)
Linksys Wireless-G Router (WRT54G v4)

For a while there, my connection was just fine, and running at a good speed, with a 70%+ connectivity... but recently, my connection seems to have dropped down to often 2 KB/sec while I usually used to DL at 150 KB/sec...

I haven't done any driver changes or anything... what could be the problem?

-----

**Here are my results from speedtest.net**
(down 503 kbps; up 282 kbps; distance ~100 mi; ping 116 ms)
[[IMG]http://www.speedtest.net/result/362319348.png[/IMG]](http://www.speedtest.net)

-----

**Here is what iwconfig gives me.**
wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:18:39:48:83:93   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=61/100  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-----

**Results for "sudo ping -f -s 1400 -w 5 192.168.1.1"**
PING 192.168.1.1 (192.168.1.1) 1400(1428) bytes of data.
.............. 
--- 192.168.1.1 ping statistics ---
112 packets transmitted, 98 received, 12% packet loss, time 3509ms
rtt min/avg/max/mdev = 13.764/263.248/340.425/59.410 ms, pipe 10, ipg/ewma 31.613/296.809 ms

---

### Post by dvkris on 2008-11-26
Topping thread for help, still not resolved...

I discovered after restarting the computer, the wireless connection seems to be really good and downloads at 100k+ kbps but after a while of the computer being on, I don't know which activities might cause it but the connection gets slowed.

---

