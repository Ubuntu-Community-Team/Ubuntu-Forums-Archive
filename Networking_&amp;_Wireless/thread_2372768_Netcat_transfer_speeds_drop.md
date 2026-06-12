---
title: "Netcat transfer speeds drop"
date: 2017-09-28
forum: Networking &amp; Wireless
---

### Post by jduskey on 2017-09-28
I am trying to transfer 1.3 TB worth of data from my old server to my new server. The network is a 1GB and the connection starts out at 111 Mbps but then drops to 40. Using iperf i get a speed of 900 Mbps. What am I doing wrong?

---

### Post by TheFu on 2017-09-29
Use rsync.
To know what you are doing wrong, you'd actually have to say what you are doing, all the hardware involved in the transfer - especially the disk drives.

BTW, netcat is terrible for security.  Terrible.  Use rsync.

---

