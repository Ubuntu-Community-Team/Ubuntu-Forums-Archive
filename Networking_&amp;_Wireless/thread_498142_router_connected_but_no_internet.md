---
title: "router connected but no internet"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by jimbocomando on 2007-07-11
I have just changed from windows to ubuntu and  now can not access the internet. Ubuntu shows that I am connected to my router, but when I open firefox I can't get on any websites. Why am I connected to my router but not the internet?

---

### Post by Mr. C. on 2007-07-11
Short on details gets you short on responses.

From the command line, what's the output of:
```

ifconfig -a
netstat -rn
cat /etc/resolv.conf
```

MrC

---

### Post by easalee on 2007-07-16
I just had the same issue -- Examined output of the three commands.

Discovered I had no /etc/resolv.conf on my Feisty Fawn box. Duplicated the contents of that file on a dapper drake box. Viola -- internet access. 

Thanks much for the hint. I have been scratching my head for two days now.

---

