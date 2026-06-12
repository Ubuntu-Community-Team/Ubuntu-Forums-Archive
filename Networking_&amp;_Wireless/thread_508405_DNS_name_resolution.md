---
title: "DNS name resolution"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Darthter on 2007-07-24
Recently install 7.04 on my laptop, but I'm experiencing a bit of an issue with DNS.

I can ping external web sites by name, but not internal machines.  Pinging by IP Address works fine, but the system cannot resolve names

The correct DNS server has been configured by the NIC.

Any ideas???

Thanks

---

### Post by kursatkaraca on 2007-07-24
Hi,
You are probably behind a Firewall and DNS resolves NATed(Network Address Translation) ip addresses to you. 

For example; A Server has a local ip of 192.168.4.1 and its NAT address to outside world is 155.155.155.155 . When use ask DNS for a domain that is hosted on that server you will get 155.155.155.155 as an answer. Your pc trying to reach that server using 155.155.155.155 but it is impossible. Because it is the ip address for outside world.

Regards...

---

### Post by Darthter on 2007-07-24
> **kursatkaraca said:**
> Hi,
You are probably behind a Firewall and DNS resolves NATed(Network Address Translation) ip addresses to you. 

For example; A Server has a local ip of 192.168.4.1 and its NAT address to outside world is 155.155.155.155 . When use ask DNS for a domain that is hosted on that server you will get 155.155.155.155 as an answer. Your pc trying to reach that server using 155.155.155.155 but it is impossible. Because it is the ip address for outside world.

Regards...

When I ping the server name (or any other PC on the internal network), my laptop cannot resolve the ip address, therefore fails.
When I ping using IP Address, it is successfull.
eg:
[INDENT]Command: ping SERVER1[/INDENT]
[INDENT]result: Fail[/INDENT]

[INDENT]Command: ping 192.168.1.1[/INDENT]
[INDENT]result: Success[/INDENT]

The DNS setting on my laptop is configured with the correct IP address of the internal DNS server.

All PCs/Servers (inc. my laptop) are within the company firewall.

If I edit my HOST file & enter the server name/ip address, the ping works, but only for that one machine.

---

### Post by ztirffritz on 2007-10-10
Did you ever find a solution to this problem?  I'm having a similar problem, but it only seems to be affecting new computers.  Computers that have been on my network since the machine was installed appear to work.  I suspect that there is a cache somewhere that is not getting cleared or updated, but everything that I read says that Linux does not cache DNS data.

---

### Post by helgman on 2007-10-10
Do you get IP address and DNS settings via DHCP?

Do you have a line saying

```
search *domain*
```

above the nameserver in **/etc/resolv.conf**?

---

