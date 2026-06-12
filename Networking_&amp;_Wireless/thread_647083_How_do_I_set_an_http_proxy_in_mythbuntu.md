---
title: "How do I set an http proxy in mythbuntu?"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by Compeek on 2007-12-21
I am struggling with a few things in mythbuntu right now, but one of the main things is that I have a proxy server here. I need to know how to set up mythbuntu so it will use the proxy server for http.

Thanks for the help. :-)

---

### Post by now-new on 2007-12-23
install squid?
it was pretty easy for me just edit some of the stuff that is there but one thing is how to create a domain I mean for the proxy liky proxy.something.net so when I go to the other pc should I do it in the network interface where the IPs are stored or where my dns is defined I mean the DNS from sbc.

---

### Post by Azrael3099 on 2008-06-24
Sorry this is rather a long time after you posted your question but perhaps others will find this helpful.

The only way I can see to do it is to go:

```
$ export http_proxy=http://user:passwd@proxy.domain.com:port/
```

(not as super user) but this needs to be done at each boot (could be done in a script).  However the mythbuntu scripts still appear not to be working (I am using the 8.04 release).

HTH

---

