---
title: "open port via port scan"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by patrik k on 2010-11-09
Was running the default port scan tool in network tools on my own IP address.
Curious as to why each time I run the scan, different ports show open, sometimes maybe just one port, other times 2-3 ports open and occasionally, no ports show open.
I understood ports were static; either open or closed depending on configs and running apps.
I am currently running ufw.
Also, in Firestarter configs, I have set ICMP filtering.
I can successfully ping my own IP address both from terminal and network tool.
Wouldn't ICMP filtering not return echo?
I obviously have forgotten something?

---

### Post by cariboo on 2010-11-09
There is a bug in the port scan tool, that we've been waiting for upstream to fix for over two years.

I would suggest using nmap, and if you need a gui zenmap, they are both in the repositories.

You are pinging the system on the internal loop interface, so it will return it. 

I would suggest if you have access to another system on your internal network you will get better and more accurate results by using it.

For example if I ping this system from another computer on my network I get the following results:

```
nmap 192.168.1.225

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-09 19:58 PST
Interesting ports on 192.168.1.225:
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
```

If I run nmap locally, this is the result I get:

```
nmap localhost

Starting Nmap 5.21 ( http://nmap.org ) at 2010-11-09 19:58 PST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00017s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 997 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
3306/tcp open  mysql
```

---

### Post by patrik k on 2010-11-09
Thanks for the great tip on Zenmap.
Neat tool.
Questions answered.
Interesting that it outputs that all 65K+ ports are closed.
Also outputs that "too many fingerprints match this host to give specific OS details"
Thanks again.

---

