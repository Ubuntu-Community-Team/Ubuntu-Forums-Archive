---
title: "Insight Needed into DNS Issue"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by antar on 2007-07-29
Okay, so I posted about this problem a week or so ago, but since then, I've honed in on the problem.

I've got a computer that I did not configure that I need to get up-and-running as a web server.

I'm at a college, and in order to get onto the network, the computer first needs to authenticate through securesmart.<college>.edu

When I first got the computer, it was working great, but suddenly, about a month ago, it refused to connect to the network. I did some research and some poking around and discovered that while it could ping the securesmart server (ping x.x.252.140), trying to ping using the domain name failed (ping securesmart.<college>.edu).

Researching more, I discovered this must be a problem with DNS.

The computer is configured to use DHCP to obtain a dynamic IP address (and it does that successfully), and my resolv.conf is fine:

```
nameserver x.x.1.2
nameserver x.x.4.12
search <college>.edu
```

I have other Ubuntu machines on the same network that are working just fine, and all the configuration files are identical.

I've tried flushing the DNS cache.

nslookup confirms that the problem is connecting to the DNS servers (reports: "connection timed out; no servers could be reached).

I'd reinstall Ubuntu, or at least use the LiveCD to authenticate the computer to the network, but the blasted thing doesn't even have a CD drive.

Does anyone know of *anything* else I can try?

Thanks.

---

### Post by bwhaley on 2007-07-29
I think there's a few additional things to try. First, check out your */etc/nsswitch.conf* file. You should see the following line:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

If you don't see dns in that line, add it.  Next, what happens when you telnet to port 53 on your DNS server? For example, in my case I get something like this (bold is my typing):

```

> **telnet 192.168.1.1 53**
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
^]**quit**

```

If you don't get a connection, make sure iptables isn't configured to deny DNS (unlikely, but possible). What does *sudo iptables -L* report? If you have any firewall rules blocking access, you'll need to add rules to permit outgoing communication on TCP and UDP port 53. 

One final step you can try is to "sniff" traffic on your interface to see what's happening at the network level:

```

> **sudo /usr/sbin/tcpdump  -i wlan0 udp port 53**
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
10:17:41.907649 IP rivendell.local.32793 > liger.domain:  11220+ A? google.com. (28)
10:17:41.908421 IP rivendell.local.32794 > liger.domain:  51066+ PTR? 1.1.168.192.in-addr.arpa. (42)
10:17:41.916784 IP liger.domain > rivendell.local.32794:  51066* 1/0/0 PTR[|domain]
10:17:41.916953 IP rivendell.local.32794 > liger.domain:  21893+ PTR? 2.1.168.192.in-addr.arpa. (42)
10:17:41.935158 IP liger.domain > rivendell.local.32793:  11220 3/0/0 A eh-in-f99.google.com,[|domain]
10:17:41.949908 IP liger.domain > rivendell.local.32794:  21893 NXDomain 0/0/0 (42)
10:17:41.950402 IP rivendell.local.32794 > liger.domain:  43300+ PTR? 99.207.14.72.in-addr.arpa. (43)
10:17:41.969783 IP liger.domain > rivendell.local.32794:  43300 1/0/0 (77)

```

In the previous command, I ran the *tcpdump* command, with *-i wlan0* (to indicate the interface I wanted to use, in most cases this is probably eth0), then udp port 53 (to listen only for UDP traffic on port 53). Then, in another window, I ran an nslookup for google.com. The output is the DNS conversation that followed. You should see communication in both directions. Above, rivendell is my local machine and liger is the DNS server. You can see traffic from rivendell to liger (rivendell.local.32794 > liger.domain) and from liger to rivendell.

---

### Post by antar on 2007-08-01
Thanks a whole bunch, but I talked to a network admin who let me know it WAS my MAC address after all. Now I just need to convince him to UN-blacklist it...

Mystery solved.

---

