---
title: "Network speed about 50% slower than it should be"
date: 2017-10-09
forum: Networking &amp; Wireless
---

### Post by dstaley on 2017-10-09
I have a gigabit fiber connection with symmetrical download/upload.  I'm experiencing an issue where Speedtest.net reports download speeds  less than 50% of the upload speed result. My download speed is hovering  between 300-400 Mbps, whereas my upload speed is consistently over 900  Mbps.
  
I've confirmed it's not an issue with my connection by plugging the  ethernet cable that goes into my Ubuntu box into a MacBook Pro, where  I'm getting the expected result (800 Mbps download, 800 Mbps upload). I've tested the connection between the Ubuntu server and my  MacBook Pro using iperf3, where I got near full gigabit speeds on both  download and upload. Finally, I've confirmed it's not an issue with my NIC by reproducing the issue on a known-good USB3 Gigabit ethernet adapter.
 

Any ideas as to why my download speed is much lower than it should be?

---

### Post by wildmanne39 on 2017-10-09
*Thread moved to **Networking & Wireless for a better fit**.*

---

### Post by HermanAB on 2017-10-10
You'll have to play with iperf, ethtool and tcpdump to get some idea of what is going on.

---

