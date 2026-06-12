---
title: "[SOLVED] DNS resolution error on local network"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by josir on 2008-07-07
Hi folks, 

I have a weird problem with DNS resolution on a specific machine that don't recognize .local machines.

I have a local DNS 192.168.0.1 working fine with Linux and Windows clients. But on this Ubuntu 8.04 machine, it does not work.

$> cat /etc/resolv.conf
nameserver 192.168.0.1

$>nslookup wiki.local

Server:		192.168.0.1
Address:	192.168.0.1#53

wiki.local	canonical name = linux05.local.
Name:	linux05.local
Address: 192.168.0.5

[B]$>ping wiki.local
ping: unknown host wiki.local[/B]

Probably it is a misconfiguration but I had no other ideas on how to fix it. What more can I do to find the problem?

Thanks in advance,
Josir

---

### Post by superprash2003 on 2008-07-08
are you able to ping the ip of wiki.local?

---

### Post by josir on 2008-07-08
Yes. The ping works fine even from the browser/apache.

[http://192.168.0.5](http://192.168.0.5)

---

### Post by tcpip4lyfe on 2008-07-08
what is the output of:

hostname
hostname -f

---

### Post by josir on 2008-07-08
I found the problem! A stupid guy (me) added on /etc/hostname the server ip 192.168.0.5 and put another servername.... When I remove the line on /etc/hostname, ping worked fine.

Thanks to you all!
Josir Gomes

---

### Post by webweaver on 2008-09-23
I was having a similar problem, except my fix was different.
In my /etc/nsswitch.conf file I had the following line:
```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```

Which I had to change to:
```

hosts:          files mdns4_minimal dns mdns4

```

Now I can ping other machines on the network using the local network domain.  However...  the ping is MASSIVELY slow...

My setup may be a bit different though, as I have an Ubuntu Server (8.04.1 64bit) setup as a Samba + LDAP domain controller, this has BIND9 for DNS.

Can anyone offer suggestions please?

UPDATE:
Nevermind, changing that same line again to:
```

hosts:          files dns wins

```
Has fixed me up!

---

