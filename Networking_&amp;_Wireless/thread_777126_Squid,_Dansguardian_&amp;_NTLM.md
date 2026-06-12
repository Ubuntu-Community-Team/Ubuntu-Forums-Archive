---
title: "Squid, Dansguardian &amp; NTLM"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by legsak1mbo on 2008-05-01
Hi,

We have a brand new Hardy box setup running Squid and Dansguardian and authenticating with our AD domain. All works perfectly except phrase filtering which doesn't seem to work at all. We connect through a county-wide proxy that all schools in our area use.

Here's the configuration:-

dansguardian.conf

```
filterip =127.0.0.1
filterport = 8081
proxyip = 127.0.0.1
proxyport = 3128
```

squid.conf

```
http_port 192.168.0.220:8081
http_port 127.0.0.1:3128
cache_peer 127.0.0.1 parent 8081 0 proxy-only default login=*:password
cache_peer proxy.ourcounty.org.uk parent 8080 0
```

And we have NTLM auth configured.

The clients proxies are set to 192.168.0.220:8081

Everything works perfectly, even passthrough auth but it won't filter for banned phrases.

All help gratefully received...

---

