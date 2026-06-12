---
title: "Slow Computer to Computer (WiFi to Ethernet) LAN Speed"
date: 2017-10-22
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2017-10-22
Hi everyone.  I'm having some issues with my network and could use some help.

I'm getting extremely slow SMB and NFS transfer speeds across my LAN (~2.8 MB/sec 22mb/sec).

Both server and client are running Ubuntu 16.04.  The server is connected via Ethernet and the laptop wifi (built in wireless N).  The network has as ASUS RT-AC66 AC1750 router and a gigabit switch.  All cable is Cat 5e.  When running a speed test with our internet both easily achieve the 85mb/sec delivered by our provider (well above the 22mb achieved when connected intranet).

I've run iperf -c and get 875mb/s when both are connected via Ethernet and only 22-25 mb/s when the laptop is connected via WiFi.

This seems to me a LAN issue since I can connect to the internet so much faster.  My only issue is I have on idea where to look/start.

Any help would be appreciated. Thanks!

---

