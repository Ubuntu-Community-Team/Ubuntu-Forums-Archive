---
title: "DNS lookups not working on single 12.04 Server"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by TheFu on 2014-04-02
I feel stupid.  My inbound email gateway isn't able to perform DNS lookups. This is a new issue since re-IPing the internal network over the weekend to let VPN stuff work at more places. I've looked over the config, compared it to other working servers here, but still can't figure out the issue.  It has been a few days on that server - too much spam is getting through.

* 12.04.4 Server
* Static IP
* pinging the internet by IP works fine, so this is just a DNS issue and only on that single machine.
* local DNS caching server 172.22.22.1

/etc/network/interfaces:
```
# The primary network interface
auto eth0
iface eth0 inet static
  address 172.22.22.62
  netmask 255.255.255.0
  gateway 172.22.22.1
  dns-nameservers 172.22.22.1

$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 52:54:00:b4:39:89  
          inet addr:172.22.22.62  Bcast:172.22.22.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:feb4:3989/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5112902 (5.1 MB)  TX bytes:275281 (275.2 KB)

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         rt1             0.0.0.0         UG    100    0        0 eth0
172.22.22.0     *               255.255.255.0   U     0      0        0 eth0

$ more /etc/resolv.conf 
nameserver 172.22.22.1

```

From any other machine with similar settings (different IPs), DNS is working. .1 is the local DNS caching server.
It has to be something simple. Ideas?

---

### Post by TheFu on 2014-04-02
Since posting this, it has started working again.  I didn't change anything on any of the servers here.
Basically - solved, but without any reason.  It is just scary to see DNS failures in the daily logwatch reports.
I hate it when things start working and I didn't change anything.

---

### Post by SeijiSensei on 2014-04-02
There have been reports of BIND9 randomly stopping.  Usually these are traced to memory exhaustion of some kind or perhaps a problem with thread management.  See, for instance, [http://ubuntuforums.org/showthread.php?t=2203520](http://ubuntuforums.org/showthread.php?t=2203520) and [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=205926](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=205926).

I generally put DNS and mail on the same server and resolve using localhost.

---

### Post by TheFu on 2014-04-02
Thanks for the reply.

Not running BIND here.  Only 30 servers or so - use ansible to manage /etc/hosts easily - the issue isn't with internal anything - only external DNS.

The router has a caching DNS server that is shared by all internal clients.  All other servers were able to see external DNS results, just not my email gateway box. Tested this from 3 other systems within a few seconds.  **dig google.com** - worked on them all, except the problem server.

I would keep DNS and email separate. Both are highly hacked services - I've had BIND hacked once in 2002. I was a few months behind on patches - it was a different time. These days, being 2 weeks behind on patches concerns me.

It magically started working. I don't have any good reason. Perhaps the DNS for the main provider was being attacked? I dunno. Why would it work from other systems, but not this one? They all use the same DNS caching server - that is also maintained by ansible - plus I manually checked it.

---

