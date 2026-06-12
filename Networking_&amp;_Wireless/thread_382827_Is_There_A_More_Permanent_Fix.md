---
title: "Is There A More Permanent Fix?"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by ICUR2Ys on 2007-03-12
I have to keep commenting out the first nameserve in file /etc/resolve.conf.  Is there a permanent fix for this problem.  My browser won't work with the nameserve that keeps popping up in the file.

Thanks

---

### Post by Mr. C. on 2007-03-12
This is a frequently asked question.  Configure your router to provide the correct DNS servers, and order them according to their lookup speed.  This will help you see how fast the response is emperically.
```

nslookup somedomain.com DNS_IP1
nslookup anotherdomain.com DNS_IP2
```

MrC

---

### Post by spd106 on 2007-03-12
These settings are most likely dealt out by your DHCP server, so you will have to make changes there.

(Oops, beaten to it. What Mr. C said.)

---

