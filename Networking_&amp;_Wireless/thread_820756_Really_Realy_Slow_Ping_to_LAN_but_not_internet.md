---
title: "Really Realy Slow Ping to LAN but not internet"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by nlinux on 2008-06-06
Ok, I'm pulling my hair out with this one.  My local network at work has an internal DNS server that gits issues by DHCP and works fine except for one issue.  If I try to ping any of the local LAN machines that are in that DNS, it is painfully slow.

```
# ping www.mylan.com

PING mylan.com (172.16.x.x) 56(84) bytes of data.
(about 5-10 seconds go by before the first ping starts)
64 bytes from 172.16.x.x: icmp_seq=1 ttl=127 time=2.02 ms
64 bytes from 172.16.x.x: icmp_seq=2 ttl=127 time=1.22 ms
64 bytes from 172.16.x.x: icmp_seq=3 ttl=127 time=0.800 ms
.....
64 bytes from 172.16.x.x: icmp_seq=11 ttl=127 time=0.895 ms
64 bytes from 172.16.x.x: icmp_seq=12 ttl=127 time=0.882 ms
64 bytes from 172.16.x.x: icmp_seq=13 ttl=127 time=1.06 ms

--- mylan.com ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time **93269ms**
rtt min/avg/max/mdev = 0.800/1.133/2.028/0.301 ms
```

took 93 seconds to get 13 packets pushed through even though the actual ping times are right where they should be!!!!

If I ping the site by IP and not name it works fine too!

```
#ping 172.16.x.x
PING 172.16.x.x (172.16.x.x) 56(84) bytes of data.
64 bytes from 172.16.x.x: icmp_seq=1 ttl=127 time=1.70 ms
64 bytes from 172.16.x.x: icmp_seq=2 ttl=127 time=1.18 ms
64 bytes from 172.16.x.x: icmp_seq=3 ttl=127 time=1.24 ms
64 bytes from 172.16.x.x: icmp_seq=4 ttl=127 time=1.12 ms
64 bytes from 172.16.x.x: icmp_seq=5 ttl=127 time=1.03 ms
64 bytes from 172.16.x.x: icmp_seq=6 ttl=127 time=1.14 ms
64 bytes from 172.16.x.x: icmp_seq=7 ttl=127 time=1.17 ms

--- 97.66.241.23 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 5997ms
rtt min/avg/max/mdev = 1.031/1.229/1.707/0.206 ms
```



Now if I ping an internet site or any site that's not on my local network by name it works great...

```
#ping www.google.com
PING www.l.google.com (72.14.205.147) 56(84) bytes of data.
64 bytes from qb-in-f147.google.com (72.14.205.147): icmp_seq=1 ttl=240 time=67.4 ms
64 bytes from qb-in-f147.google.com (72.14.205.147): icmp_seq=2 ttl=240 time=70.4 ms
64 bytes from qb-in-f147.google.com (72.14.205.147): icmp_seq=3 ttl=240 time=66.8 ms
64 bytes from qb-in-f147.google.com (72.14.205.147): icmp_seq=4 ttl=240 time=67.4 ms
64 bytes from qb-in-f147.google.com (72.14.205.147): icmp_seq=5 ttl=240 time=66.5 ms
64 bytes from qb-in-f147.google.com (72.14.205.147): icmp_seq=6 ttl=240 time=67.1 ms
64 bytes from qb-in-f147.google.com (72.14.205.147): icmp_seq=7 ttl=240 time=67.2 ms
64 bytes from qb-in-f147.google.com (72.14.205.147): icmp_seq=8 ttl=240 time=68.5 ms

--- www.l.google.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 6998ms
rtt min/avg/max/mdev = 66.524/67.704/70.484/1.199 ms
```


This appears to be Hardy Specific at the point.  I can walk up to any other machine in the office and get very normal results for my pings.  I've tried Windows XP, Vista, Mac Os X, and an old Fedora Core 1 box and all of them respond fine.  We have 3 Hardy Workstations and 1 Hardy Server and it's the same issue with all of them. 

I thought it might be related to IPV6 being turned on my default, but turning it off didn't seem to have any effect.  

Then I thought that the local DNS might be the issue, but doing nslookup on local or remote sites, is pretty much instantaneous, and they all resolve with my local DNS.

Anyone have anymore ideas, because even though it works, it's quite painful to use it.

---

### Post by linux6994 on 2008-06-06
If you are behind a router then you should have your IP GW and DNS the address of it. Your router will handle the dns and gw function.

Go to SYSTEM > Network Tools also

---

### Post by nlinux on 2008-06-06
> **linux6994 said:**
> If you are behind a router then you should have your IP GW and DNS the address of it. Your router will handle the dns and gw function.

Go to SYSTEM > Network Tools also


Server doesn't have a gui ;) so those tools are not any good, but the command line versions work well.  My router is also set up not to do Dnsmasqing as we need internal DNS servers.  I doubt this is the issue anyway as nslookup works fine and established connections don't have latency issues.  It almost appears to be isolated to the PING command.

---

### Post by syx on 2008-12-16
ive got the same problem with 8.10.

My dhcp and dns server is a windows 2k3 r2 box.

takes around 6 seconds to respond to each ping but the time result is around .1 second.

Did you end up resolving your issue ?

---

### Post by Joe Momma on 2009-10-13
I have the same issue, ping by name is slow, ping by ip is fast.  However, pinging through the network tools gui does not have this problem.  It is only slow by name from the command line.

Any ideas why this would be?

Edit:

It seems that "ping -n" speeds things up tremendously.  So my problem is solved, but now I want to understand this if anyone cares to explain.

Also I seem to have similar slowdown problems with ssh by name vs ip.  Is there an analogous "-n" option for ssh?

---

### Post by Iowan on 2009-10-13
At the risk of sounding obvious - name resolution seems to be working slowly. I converted my DHCP server to DNSMasq to gain the DNS/DHCP link, and my response time improved dramatically. Having it on a P3/400 versus a P-Pro/200 probably didn't hurt, either.

---

