---
title: "FQDN for nameserver"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by m_a2 on 2014-08-15
Hello,

I am looking for the FQDN for my name server and my name servers ip address.

Can someone please guide me on how am I able to find these using terminal?

Thank you

---

### Post by TheFu on 2014-08-15
**more /etc/resolv.conf**
that should have the IP.  Using DNS names for a nameserver is NOT DONE.  Of course, network-manager may do something completely different. I don't use it.

---

### Post by SeijiSensei on 2014-08-15
Assuming the nameserver is on the public internet, after you get its IP address, you can try:
```
host ip.that.you.found
```
If the host is properly configured with both forward and reverse nameservice, you'll get the server's name in response.

```

Seiji@GhostWorld:~$ host 8.8.8.8
8.8.8.8.in-addr.arpa domain name pointer google-public-dns-a.google.com.

Seiji@GhostWorld:~$ host google-public-dns-a.google.com
google-public-dns-a.google.com has address 8.8.8.8
google-public-dns-a.google.com has IPv6 address 2001:4860:4860::8888


```

---

