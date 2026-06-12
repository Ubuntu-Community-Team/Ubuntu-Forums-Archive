---
title: "no arp ping?"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by transwarp on 2008-11-01
I've had this problem with hardy as well as intrepid. On a fresh default install, with a direct wired connection (I don't have a personal router/firewall setup), I periodicly get logged out by cisco's clean access some time after logging in. After checking with the university IT dept and noting the times this occurred and my mac address and IP, they checked their logs and found:

**My ubuntu system wasn't returning an arp ping**, and so cisco thought it was disconnected and logged me out even though I had internet traffic going through.

**Verifying this I arp pinged 127.0.0.1 and it tried and just hung waiting for a response.** Regular pings go through fine, and internet access while logged in is fine. I can arp ping other devices with no problems.

I also tried turning off IP TABLES with no effect, so the problem seems farther in. 

I also posted [a bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291297") 

anyone have input on this?

---

### Post by Tanvir on 2009-11-18
I am also having the same problem. Cisco Clean Access server also logs me out after about 15-20 mins. Have you solved the problem?

---

