---
title: "Wireless Network Throughput Problem"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by kidcharles on 2008-05-21
I just recently upgraded my computer with a wireless adapter card from 7.04 to 8.04, and now have a serious network throughput problem. Okay, here is my setup, bear with me:

3 computers, 1 wireless/wired router

Computer 1 (8.04): Wired connection to router OR wired connection direct to Computer 2
Computer 2 (8.04): Wireless connection to router AND wired connection to Computer 1
Computer 3 (7.04): Wireless connection to router

Tested using iperf:

Speed test between C1 and C3 (wireless): 12 Mbps
Speed test between C1 and C2 (direct wired): 90 Mbps
Speed test between C1 and C2 (wireless): 150 kbps
Speed test between C3 and C2 (wireless): 150 kbps

Therefore, the wireless router is working fine, since I can get 12 Mbps through the wireless connection to C3. Also, the networking as a whole is working okay on C2, since I can get a massive 90 Mbps through the wired connection to C1. However, there is obviously a problem with the wireless connection on C2, since I can only get a measly 150 kbps through the wireless connection on C2. The throughput was fine with this setup in 7.04, now it is bad in 8.04. Any ideas on how to troubleshoot this? Thanks.

---

