---
title: "PPTP-Setup &quot;Connection established&quot; in netstat, but then times out"
date: 2017-05-08
forum: Networking &amp; Wireless
---

### Post by neokil on 2017-05-08
Hello guys,

I am currently trying to set up a pptp-vpn. I followed step 1-4 on [this]("https://www.digitalocean.com/community/tutorials/how-to-setup-your-own-vpn-with-pptp") tutorial.
When I am trying to connect to the vpn-server using my windows 10 laptop I am timing out.
I checked the netstat before connecting using "netstat -alpn | gre :1723" and got 1 entry 
```
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN      7537/pptpd
```
after connecting there are 2
```
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN      7537/pptpd

tcp        0      0 85.214.XX.XXX:1723      46.223.XX.XXX:47514       ESTABLISHED 7581/pptpd [46.223.

```
The state of the second entry will switch to "TIME_WAIT" after a few moments.

What am I doing wrong?


Greetings
Simon Schulte | Neokil

---

### Post by viejillo on 2017-10-14
**apologies misread your question.**

---

