---
title: "How do I load the ip_queue module?"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by Krusader3z on 2007-12-15
I have peer guardian installed but when i try and monitor the status, i get this error

Reading blocklist
detected ASCII blocklist
Entering daemon mode
Allowing all traffic on port 80
Blocking 188776 ranges (744699856 IP addresses)
**ipq_set_mode failed; is the ip_queue kernel module loaded?**

---

### Post by heindsight on 2007-12-15
try:
sudo modprobe ip_queue

---

