---
title: "Can ping/host but cannot traceroute/access internet"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by darlliu on 2008-04-27
Hi, I've got a network problem since I tried to install different distros of linux on my old laptop.

The installation and all that seem fine to me. No hardware problems and the system can connect via DHCP. I can ping and host different internal/external ips/sites but I cannot access the internet except for the firefox startup page(it loads pretty fast) and sometimes, google. Traceroute returns no result either.

This problem is very annoying, I wonder what has gone wrong?

I've already googled and tried to solve this myself, the best I could come up with is something with window scaling, I tried setting that to 0 but it didn't help.

thx

---

### Post by superprash2003 on 2008-04-27
you might want to try changing your DNS servers to opendns. read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by darlliu on 2008-04-27
> **superprash2003 said:**
> you might want to try changing your DNS servers to opendns. read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Thank you for your reply.

I've done setting up a static ip and changing my dns to opendns and I still have this problem. 

I use an adsl modem and a router, should I try connecting directly to the adsl? but my other PCs (one xp one vista) are doing fine.

---

### Post by superprash2003 on 2008-04-27
ok .. this is really strange.. ping works but it wont load.. hmm.. yea you could try connecting directly just to test it out

---

### Post by kevdog on 2008-04-27
What does route -n say?

---

### Post by darlliu on 2008-04-27
> **kevdog said:**
> What does route -n say?

route -n says
```
192.168.1.0 0.0.0.0      255.255.255.0 U 0 0 0 eth0
127.0.0.0   0.0.0.0      255.0.0.0     U 0 0 0 lo
0.0.0.0    192.168.1.1   0.0.0.0      UG 0 0 0 eth0
```

---

### Post by darlliu on 2008-04-28
so I tried to directly connect via adsl too. and it didn't work. ugh

route -n says 
```

218.20.52.1  0.0.0.0  255.255.255.255  UH 000 dsl0
169.254.0.0  0.0.0.0  255.255.0.0      U  000 eth0
127.0.0.0    0.0.0.0  255.0.0.0        U  000 lo

```

but then I already got everything I need on this old laptop from the DVD now. So maybe I can just leave it at that.

---

