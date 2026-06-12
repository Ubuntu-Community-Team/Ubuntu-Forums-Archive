---
title: "Problems with DNS PPP"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by xenar on 2008-05-05
Hello, there is a connection via CDMA for PPP. Connect normally(GNOME-PPP), DNS in resolv.conf set too well, working through the console and ping, wget, nslookup as well as with IP addresses with domain. BUT is run any Internet-GUI program so immediately locked all, the connection hangs in the browser but will not open (tried as IP addresses and domain) in the console also all "die" (wget, ping, nslookup). The connection speed drops to 110 b / sec.

Judging by the ping that what is happening at this moment with dns

```
64 bytes from ya.ru (213.180.204.8): icmp_seq=144 ttl=58 time=137 ms
64 bytes from ya.ru (213.180.204.8): icmp_seq=145 ttl=58 time=114 ms
64 bytes from ya.ru (213.180.204.8): icmp_seq=146 ttl=58 time=128 ms
64 bytes from ya.ru (213.180.204.8): icmp_seq=147 ttl=58 time=121 ms
64 bytes from ya.ru (213.180.204.8): icmp_seq=148 ttl=58 time=153 ms
64 bytes from 213.180.204.8: icmp_seq=149 ttl=58 time=350 ms
64 bytes from 213.180.204.8: icmp_seq=150 ttl=58 time=214 ms
```

Helps only reconnect. I do not know how to overcome this problem. Help please

PS Sorry for the bad English

PSS OS Ubuntu 8.04

---

### Post by superprash2003 on 2008-05-05
you could try changing your DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by xenar on 2008-05-06
> **superprash2003 said:**
> you could try changing your DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

	
Unfortunately this did not help solve the problem. Are there any other options?

---

