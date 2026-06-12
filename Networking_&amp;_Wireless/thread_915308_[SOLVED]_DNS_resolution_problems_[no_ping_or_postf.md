---
title: "[SOLVED] DNS resolution problems [no ping or postfix, yes dig and nslookup]  off and"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by kraftbj on 2008-09-09
New ubuntu user here.

I've recently setup an ubuntu box to server as an outbound e-mail relay for my non-profit org using Postfix.

Randomly throughout the day, e-mails will be suspended in the queue with "(Host or domain name not found. Name service error for name=sbcglobal.net type=MX: Host not found, try again)" type errors. All domains impacted.

During these times, I am unable to ping any domain, but pinging IP addresses work fine.

During these times, nslookup and dig function without problem.

While this was happening, I switched from my ISP (TW Telecom) DNS servers to OpenDNS with no impact.

After about 20 minutes or so, everything will start to function again as normal.

Any ideas?

/etc/resolv.conf
```
nameserver 208.67.222.222
nameserver 208.67.220.220

```

/etc/network/interfaces
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.123.8
netmask 255.255.255.0
gateway 192.168.123.1

auto eth0

auto eth0:1

iface eth0:1 inet static
address 216.xxx.xxx.xxx #masked for public post
netmask 255.255.255.248
gateway 216.xxx.xxx.xxx #masked for public post

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.123.8  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: [address listed] Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7216429 (6.8 MB)  TX bytes:3763638 (3.5 MB)

eth0:1    Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:216.xx.xx.xx  Bcast:216.xx.xx.xx  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24125 (23.5 KB)  TX bytes:24125 (23.5 KB)

```

Thanks!
Kraft

---

### Post by doas777 on 2008-09-09
I would check with your ISP. DNS failures are likely on their end. you can also find public dns server addresses that you can fall back on in times of trouble. since they are potentially far away (geographically) so using them exclusively may increase your time-to-post.

good luck,
Franklin

---

### Post by kraftbj on 2008-09-09
This has been happening throughout the day while using OpenDNS.

I haven't used them before today, so I don't know if downtime is common.

Also, excuse my ignorance, but would nslookup and dig still function is DNS servers are down? My understanding says no, but I'm not trained in this area.

[Update: Also, other computers on the same network/router/DNS server work without interruption.]

Thanks,
Brandon

---

### Post by kraftbj on 2008-09-10
Okay, I played around with it quite a bit tonight.

No matter what I did with DNS servers, there was no change in result. I've used my ISP's, OpenDNS and the 4.2.2.x series.

After looking around for awhile, I ran
```
sudo ip route flush cache
```

Presto. Everything in the queue went out without a problem.

Any ideas on what led to an issue that would be resolved by flushing the IP routing?

More importantly, any ideas on how to prevent this from happening again? :-)

Thanks everyone. I really appreciate any insight.
Brandon

---

### Post by kraftbj on 2008-09-10
Latest news.

To test, I changed to a different static IP address (192.168.123.95 instead of 192.168.123.8) and everything worked fine.

I added the eth0:1 of my public address (216.xxx.xxx.xxx) to that, with everything working fine.

I switched back to the original static IP address (.8) resulting in outbound traffic not flowing through.

Finally, I setup my /etc/network/interfaces to have eth0 on .8, eth0:1 on the public IP and eth0:2 on the other static IP that worked before:
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.123.8
netmask 255.255.255.0
gateway 192.168.123.1

auto eth0

auto eth0:1

iface eth0:1 inet static
address 216.xx.xx.xx
netmask 255.255.255.248
gateway 216.xx.xx.xx

auto eth0:2
iface eth0:2 inet static
address 192.168.123.95
netmask 255.255.255.0
gateway 192.168.123.1

```

With that, everything seems to be working fine. Yesterday, the previous configuration (static .8 with public IP on eth0:1) worked for awhile, then, without any changes on the box, went out.

My guess now is that there's a router issue that was preventing outbound traffic from internal 192.168.123.8 from passing through the router. 

The telecom controls the router, so I don't have direct access to check settings. If this happens again with the new static IP address, I'll give them a call.

---

