---
title: "Help with Guarddog protocol rules"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by 67GTA on 2007-08-29
I installed Guarddog, and have everything setup except for one website. I have a satellite connection for my internet with a usage limit(FAP). The website that my ISP uses to show your usage will not load now. Guarddog is set to log activity, so I looked in /var/log/syslog, and saw where the activity had been dropped every time I try to view the website. The problem is that I have no clue what protocol the site uses. Can someone tell me by looking at the log or happen to know what protocol needs to be allowed?

Aug 29 14:01:25 fastback kernel: [62844.452000] DROPPED IN= OUT=eth0 SRC=192.168.0.100 DST=216.126.204.113 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=30689 DF PROTO=TCP SPT=5430 DPT=8488 SEQ=1603619939 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307)

---

### Post by 67GTA on 2007-08-31
Actually the connection is being dropped on the way out according to the log. How can I see what port it is trying to use? Maybe it just needs to be opened.

---

