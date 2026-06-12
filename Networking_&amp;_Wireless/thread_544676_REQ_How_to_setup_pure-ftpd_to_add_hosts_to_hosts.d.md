---
title: "REQ: How to setup pure-ftpd to add hosts to hosts.deny"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by 3rods on 2007-09-06
Can anyone recommend a good way to automatically add repeated, failed login attempts to my FTP to hosts.deny? 

Here is a sample of my syslog:

```
Sep  6 12:30:51 user pure-ftpd: (?@000-063-360.area3.spcsdns.net) [INFO] New connection from 000-063-360.area3.spcsdns.net
Sep  6 12:30:51 user pure-ftpd: (?@000-063-360.area3.spcsdns.net) [WARNING] Authentication failed for user [dick]
Sep  6 12:32:51 user pure-ftpd: (?@000-063-360.area3.spcsdns.net) [INFO] Logout.

```

I have denyhosts installed, but this only seems to work if the attacker tries to brute the ssh first, then I can deny all. Is there anything that works with FTP or other services? 

I'm not worried about eventual DoS because I have physical access to the box. 

I've heard of IPTABLES and I hear it's better to drop the packets to save bandwidth, but I'm not really sure how to automate that either.

Any help would be, well, helpful..:p

---

### Post by 3rods on 2008-01-21
Just a follow up on this. I've been using OSSEC to handle automatic additions to IPTABLES and hosts.deny files. It works very well. It also monitors your log files and notifies you if there are any issues. 

(from memory) 

IPTABLES -l     ----lists rules

IPTABLES -d INPUT 1 ---- Drops the first rule in the INPUT list from above

I believe the -a switch adds to the interface, 

Just FYI and all.

---

