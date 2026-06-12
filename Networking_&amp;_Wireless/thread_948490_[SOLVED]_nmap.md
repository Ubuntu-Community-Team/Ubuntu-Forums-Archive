---
title: "[SOLVED] nmap"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by hca on 2008-10-15
On my home LAN I at the moment have 3 computers up and running: 192.168.1.1 (router), 192.168.1.172 (PC with ubuntu 8.04 64 bits), and 192.168.1.134 (PC with ubuntu 7.10 32 bits).
When I run nmap -sP 192.168.1.* on 192.168.1.172 I can see 192.168.1.134.
When I run nmap -sP 192.168.1.* on 192.168.1.174 I can  NOT see 192.168.1.172.
WHY NOT?

Any info is much appreciated
/Hans Christian Andersen, Denmark

---

### Post by nixscripter on 2008-10-15
From the nmap manual page:

> 
The -sP option sends an ICMP echo request and a TCP packet to port 80 by default. **When executed by an unprivileged user,** a SYN packet is sent (using a connect() call) to port 80 on the target.


So if you don't run it as root, it won't actually ping. If 192.168.1.172 is dropping packets on port 80 (perhaps due to a firewall), it will not appear. Try running the command as root (with sudo) and see if it shows up.

---

### Post by hca on 2008-10-15
Thank you for a very quick reply which was just the answer on my question.
If I don't learn something new every day the time is lost!
/Hans Christian

---

### Post by nixscripter on 2008-10-15
Great. Please mark this thread as solved (under thread tools).

---

