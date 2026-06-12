---
title: "How to Permanently Adjusting UFW Rate Limiting?"
date: 2015-06-30
forum: Networking &amp; Wireless
---

### Post by john423 on 2015-06-30
Hello,

When attempting to setup knockd, I noticed that UFW was blocking my attempts to successfully 'knock' the host by introducing rate limiting.

```
Jun 30 20:09:41 ubuntu kernel: [  142.241515] [UFW BLOCK] IN=eth0 OUT= MAC=00:0d:2c:52:f8:2c:00:0c:29:4c:02:a9:08:00 SRC=EXTERNAL_IP DST=INTERNAL_IP LEN=60 TOS=0x14 PREC=0x00 TTL=49 ID=44955 DF PROTO=TCP SPT=54408 DPT=1401 WINDOW=14600 RES=0x00 SYN URGP=0 
```

After a bit of googling around, I found some suggestions to modify ```
/lib/ufw/user.rules
```

After adjusting the default limit (--limit 3/min --limit-burst 10) to something a bit more reasonable (--limit 10/min --limit-burst 25) everything worked until I rebooted the host. At that point, it appears my modified user.rules is replaced by the default version and I'm back to being rate limited.

Does anyone have any ideas on how to adjust this permanently while still using rate limiting and UFW? 

Thank you in advance!

---

### Post by dino99 on 2015-06-30
if you google around 'linux/ubuntu/kubuntu knockd ufw' you will find a few threads explaining the relationship. Modifying /lib/ufw/user.rules seems not being the good place.
[http://www.chakrityau.com/?p=59&lang=en](http://www.chakrityau.com/?p=59&lang=en)

---

