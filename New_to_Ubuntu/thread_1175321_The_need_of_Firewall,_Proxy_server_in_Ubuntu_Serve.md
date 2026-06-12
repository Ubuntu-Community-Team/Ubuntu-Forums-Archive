---
title: "The need of Firewall, Proxy server in Ubuntu Server with ADSL modem router"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by televisi on 2009-06-01
Hi all,
At the moment, this is my setting:

```
Internet => ADSL Modem Router => Ubuntu Server
                       |
                       |
                       |-------> 15 clients
```

The purpose of this Ubuntu Server is:
- File Server (using Samba)
- DHCP Server

Now the question:
- Do I really need firewall considering I'm behind ADSL Modem Router (which in this case only open specific port, ie: SSH)
- Considering these clients connect to ADSL modem router straight away, will it make a different in having proxy server? (ie: caching some frequently open site)

Thanks heaps

---

### Post by nandemonai on 2009-06-01
> **televisi said:**
> Hi all,
At the moment, this is my setting:

```
Internet => ADSL Modem Router => Ubuntu Server
                       |
                       |
                       |-------> 15 clients
```

The purpose of this Ubuntu Server is:
- File Server (using Samba)
- DHCP Server

Now the question:
- Do I really need firewall considering I'm behind ADSL Modem Router (which in this case only open specific port, ie: SSH)
- Considering these clients connect to ADSL modem router straight away, will it make a different in having proxy server? (ie: caching some frequently open site)

Thanks heaps

1. Yes and no. Does the Router have an inbuilt firewall? Might want to block incoming ICMP etc. Otherwise no, not really.

2. Yes, IF you set the clients to use the proxy. :)

3. You may also want to look into DenyHosts for SSH.

---

### Post by televisi on 2009-06-01
1. it is the normal ADSL modem router from the ISP (Netcomm ADSL Router)
2. As at the moment, I only use 1 NIC in Server, will clients be able to detect that there is proxy server in Ubuntu server and use it? (obviously I've configured all clients by DHCP setting to have gateway of my Ubuntu Server); I suspect I need transparent Proxy server, like Squid?

Thanks

> **nandemonai said:**
> 1. Yes and no. Does the Router have an inbuilt firewall? Might want to block incoming ICMP etc. Otherwise no, not really.

2. Yes, IF you set the clients to use the proxy. :)

3. You may also want to look into DenyHosts for SSH.

---

