---
title: "Half upload speed"
date: 2019-01-13
forum: Networking &amp; Wireless
---

### Post by madsere on 2019-01-13
I can only push about 50 mbps on this Gigabit link.  Download is fine, 100 mbps:

> Retrieving speedtest.net configuration...
Testing from xxx ...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by xxx  (xxx) [58.22 km]: 5.642 ms
Testing download speed................................................................................
Download: 114.96 Mbit/s
Testing upload speed......................................................................................................
Upload: 53.65 Mbit/s

The speedtest results have been confirmed by scp and sftp up/downloads.

Ubuntu 18.04.1 LTS (headless server install) on a QOTOM Q190G4.

Wired through Gigabit router to 100 mbps symmetric fiber

ethtool reports 
        Speed: 1000Mb/s
        Duplex: Full

[    2.862235] igb: Intel(R) Gigabit Ethernet Network Driver - version 5.4.0-k

The box have 4 ports, I've tried from all ports, always the same result, 

There is no load on the box worth mentioning, and iptables has been disabled during testing.

If I plug the same network cable into a laptop I get 100 mbps both up and down.  This and the above has been tested over several days and is really limited to the Qotom box. 

At my wits end here, any ideas what could be causing this?

---

### Post by madsere on 2019-01-20
Tumbleweed ....

---

