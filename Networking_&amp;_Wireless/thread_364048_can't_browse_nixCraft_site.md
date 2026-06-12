---
title: "can't browse nixCraft site"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by towsonu2003 on 2007-02-17
This is weird. [I have a post similar to this one for another website]

All web sites can be accessed just find. 

I am trying to access [www.cyberciti.biz](www.cyberciti.biz) (website for nixCraft where nice linux tutorials are posted) but I cannot if my firewall is up. for some reason, when I try to connect to the website, the website starts hitting me at random ports and I don't see any web pages. See the screenshot where I'm trying to open the website and firestarter reports hits...

I don't want to fiddle with my firewall for this one site, especially bc I don't know what it's doing with my ports :)

Can anyone tell me why this is happening? 

I am emailing the author but I doubt s/he'll help (webmasters are usually too busy to solve isolated user-problems)... 

thanks a lot :)

Edit: s/he's trying to help :) nice webmaster

---

### Post by towsonu2003 on 2007-02-19
Here is the lines from /var/log/messages when I try to browse the site:
```
Feb 19 16:50:16 localhost kernel: [17187218.356000] Inbound IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=75.126.43.232 DST=my.ip.addr.ess LEN=44 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=46432 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Feb 19 16:50:19 localhost kernel: [17187221.340000] Inbound IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=75.126.43.232 DST=my.ip.addr.ess LEN=44 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=46432 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Feb 19 16:50:19 localhost kernel: [17187221.524000] Inbound IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=75.126.43.232 DST=my.ip.addr.ess LEN=44 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=46432 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Feb 19 16:50:25 localhost kernel: [17187227.340000] Inbound IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=75.126.43.232 DST=my.ip.addr.ess LEN=44 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=46432 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Feb 19 16:50:25 localhost kernel: [17187227.520000] Inbound IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=75.126.43.232 DST=my.ip.addr.ess LEN=44 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=46432 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Feb 19 16:50:37 localhost kernel: [17187239.340000] Inbound IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=75.126.43.232 DST=my.ip.addr.ess LEN=44 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=46432 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Feb 19 16:51:01 localhost kernel: [17187263.352000] Inbound IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=75.126.43.232 DST=my.ip.addr.ess LEN=44 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=46432 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Feb 19 16:51:05 localhost kernel: [17187267.552000] Inbound IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=75.126.43.232 DST=my.ip.addr.ess LEN=44 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=46432 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
Feb 19 16:51:11 localhost kernel: [17187273.548000] Inbound IN=eth1 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=75.126.43.232 DST=my.ip.addr.ess LEN=44 TOS=0x00 PREC=0x20 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=46432 WINDOW=5840 RES=0x00 ACK SYN URGP=0 

```

---

### Post by towsonu2003 on 2007-03-11
solution here: [http://ubuntuforums.org/showthread.php?p=2282756#post2282756](http://ubuntuforums.org/showthread.php?p=2282756#post2282756)

---

