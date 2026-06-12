---
title: "Slow resolving with or without ipv6"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by pgilmon on 2008-05-07
Hi all,

I am experimenting an extremely slow dns resolution on Ubuntu 8.04. I have already tried disabling ipv6 in Firefox, in /etc/modprobe.d/aliases and even adding ipv6 module to /etc/modprobe.d/blacklist. No combination of them solves the issue.

It is a system-wide problem, since issuing a 'dig' command can take up to 10 seconds. However, and this is quite surprising, according to 'dig', the server response time is always around 50ms. Also, the server that sends the response is the primary dns set up in /etc/resolv.conf.

I have two other computers on the same network, one with vista and the other one with XP, both with the same DNS servers as ubuntu. DNS resolution is apparently instantaneous in both (and it is not a caching issue, since it is also that fast when resolving for the first time).

I would appreciate any help on this, because it just makes surfing the insanely slow.


Thanks

---

### Post by prshah on 2008-05-07
> **pgilmon said:**
> Hi all,

I am experimenting an extremely slow dns resolution on Ubuntu 8.04. 

See my (solved) thread on [http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox](http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox)... does it help?

---

### Post by pgilmon on 2008-05-07
Hi and thanks for your reply,

I have tried setting the MTU to other values by using

```
sudo ifconfig eth1 mtu XXX
```

(being eth1 the interface I'm connecting through). I have tried 1500, 1492, 1000, 2000... the results are just the same regardless which value I set up. It doesn't seem to affect dns resolving times.

Just in case it might be of any help, I am attaching the output of 'ifconfig':

```

eth0      Link encap:Ethernet  HWaddr 00:16:d4:06:00:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:13:02:43:86:05  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23031452 (21.9 MB)  TX bytes:2583184 (2.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.1 KB)  TX bytes:1200 (1.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-43-86-05-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by prshah on 2008-05-07
> **pgilmon said:**
> Hi and thanks for your reply,
I have tried setting the MTU to other values by using
```
sudo ifconfig eth1 mtu XXX
```
(being eth1 the interface I'm connecting through). I have tried 1500, 

Please re-read; the MTU is to be changed on the router, _not_ your system. And the change does not affect your windows browsing experience.

---

### Post by pgilmon on 2008-05-08
OK, I'll try that later when I'm home. Although I'm afraid it might get complicated since I also have TV over my ADSL connection (you know, the so called triple-play), and my router's configuration has to be made through the internet provider's portal rather than accessing the router directly.

In any case, thanks for your advice.

---

### Post by pgilmon on 2008-05-10
I have solved this. I just followed the isntructions [here]("http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/") for dnsmasq installation as a dns cache. Now it works like a charm. 

I know that, since this is a cache, the first time a site is resolved it should take as long as without the cache, but the plain fact is that now the resolving time is unnoticeable even the first time a site is resolved. I don't know why, but that's the way it is. Perhaps dnsmasq is using another configuration for resolving new sites?...


In any case,

---

