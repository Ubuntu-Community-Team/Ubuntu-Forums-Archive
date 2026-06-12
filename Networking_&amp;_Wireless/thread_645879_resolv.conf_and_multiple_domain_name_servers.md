---
title: "resolv.conf and multiple domain name servers"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by pmgeahan on 2007-12-20
Folks - 

I have an Ubuntu machine that sits across three networks.  For ease of reading, lets call them anet, bnet and cnet.  

The machine has three interfaces, one each for anet, bnet and cnet, and an IP on each network.  There are machines on each network that I need to be able to reach.  Each network has it's own separate DNS server.  

Here's my issue - I can't seem to get Ubuntu to check all three DNS servers for values.  For instance if I run the following command:

```
host pmg.cnet
```

I get the following answer:

[CODEHost pmg.cnet not found: 3(NXDOMAIN)][/CODE]

However, if I specify the DNS server:

```
host pmg.cnet $CNET_DNS_IP
```

I get the response:

```
pmg.cnet has address $IP
```

...so I have access to the DNS server, no problem; I just can't seem to get Ubuntu to check it automatically.

My resolv.conf:
```

search anet bnet cnet
nameserver 192.168.8.240
nameserver 192.168.4.240
nameserver 192.168.1.240

```

I have tried moving the nameserver entries around, and it seems that Ubuntu will only contact the first one in the list.  

Can anyone offer some advice?  

Thanks!

---

### Post by stroyan on 2007-12-20
You could install the bind9 package and configure a dns server on the system.
Then you could use /etc/bind/named.conf.local to specify slave zones that point to
each of the three master DNS servers.

---

### Post by jasutton on 2008-01-25
I'm sorry...you shouldn't have to start a DNS server on your system just to query DNS servers.  That is merely a work-around for a flaw in how DNS resolution takes place in Ubuntu.  The man page for resolv.conf shows that if multiple nameservers are listed in resolv.conf (up to 3), that the system will query each one in the order listed until it finds a match (or until a given timeout).

Should a bug be filed on this?

---

### Post by sergiusens on 2008-02-11
IIRC if the server returns NOT FOUND, the next server will not be queried, it will only do so if it times out.

---

