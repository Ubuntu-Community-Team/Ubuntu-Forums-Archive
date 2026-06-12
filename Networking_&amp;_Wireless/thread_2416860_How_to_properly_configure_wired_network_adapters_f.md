---
title: "How to properly configure wired network adapters for remote desktop usage?"
date: 2019-04-16
forum: Networking &amp; Wireless
---

### Post by luckydemon777 on 2019-04-16
I have an laptop running Ubuntu 18.04 and nvidia jetson tx2 (developer board that also running ubuntu 18.04, so I will count it as second pc). I tried to use remote desktop from jetson tx2 on laptop, while board was connected to router through wire and laptop through wi-fi. It works fine (except the issue with desktop environment). Than, I tried to connect board straight to laptop through wire. I configured board's adapter to 10.0.0.10/24 and laptop to 10.0.0.11 in /etc/network/interfaces file. And with configuration I cannot use remote desktop (but able to connect via ssh). Primaly, because switch "screen sharing" in settings on board automatically turning off. I saw some posts about this problem, but given solutions doesnot work for me.
So, the question is how to properly configure wired network adapters for remote desktop usage between two PC from the ground?

---

