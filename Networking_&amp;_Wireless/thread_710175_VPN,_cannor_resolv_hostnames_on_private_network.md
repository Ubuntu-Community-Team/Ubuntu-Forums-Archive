---
title: "VPN, cannor resolv hostnames on private network"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by NMA on 2008-02-28
I have the most annoying problem. I have a working VPN connection, and i can reach any host on the network by IP. However, i cannot reach any host by their hostname. Easy one i thought, it's a DNS error... BUT, my resolv.conf do in fact contain the correct DNS servers. 

Whats really strange is that i can find all host by using nslookup. Eg. nslookup <hostname> do return the correct IP, but i cannot ping that hostname. I sure can ping any host by IP. The network i conect to is a windows network

Any ideas?

---

### Post by deepclutch on 2008-02-28
may be adding hostnames in /etc/hosts helps?

---

### Post by NMA on 2008-02-29
> **deepclutch said:**
> may be adding hostnames in /etc/hosts helps?

Well, it does but it's not much of a solution if you hace several hundred hosts on a network runing DHCP...

---

### Post by Iowan on 2008-02-29
Would **winbind **or a WINS server help - or would VPN not play nice?

---

### Post by Mr. C. on 2008-02-29
> **NMA said:**
> I have the most annoying problem. I have a working VPN connection, and i can reach any host on the network by IP. However, i cannot reach any host by their hostname. Easy one i thought, it's a DNS error... BUT, my resolv.conf do in fact contain the correct DNS servers. 

Whats really strange is that i can find all host by using nslookup. Eg. nslookup <hostname> do return the correct IP, but i cannot ping that hostname...

nslookup uses its own internal resolver, not the system's resolver.  Use **dig** or **host** to test.

Is your remote host allowed to query their DNS ?  Perhaps your VPN is on a subnet that is not allowed to query their internal DNS servers.  Test by:

```
$ dig @theirDNSserverIP aHostnameOnTheirNetwork
```

---

